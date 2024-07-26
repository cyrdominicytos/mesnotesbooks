

    public List<Question>  parseQuestionsFromText(String text) throws IOException {
        CharStream input = CharStreams.fromString(text);
        QuestionAnswerLexer lexer = new QuestionAnswerLexer(input);
        CommonTokenStream tokens = new CommonTokenStream(lexer);
        QuestionAnswerParser parser = new QuestionAnswerParser(tokens);
        ParseTree tree = parser.file();
        QuestionAnswerVisitor visitor = new QuestionAnswerConcreteVisitor();
        QuestionAnswerParser.FileContext fc = parser.file();
        //System.out.println("=============fc text "+parser.pro+"==============");
        System.out.println("=============fc text "+fc.getText()+"==============");
        System.out.println("=============fc size "+fc.question().size()+"==============");
        return (List<Question>) visitor.visitFile(fc);
        //QuestionAnswerVisitor visitor = new QuestionAnswerVisitor();
        //return visitor.visit(tree);
       // return Arrays.asList();
    }


package fr.istic.m2.mcq_api.parser;

import fr.istic.m2.mcq_api.domain.Question;
import fr.istic.m2.mcq_api.parser.antlr4.QuestionAnswerParser;
import fr.istic.m2.mcq_api.parser.antlr4.QuestionAnswerVisitor;
import org.antlr.v4.runtime.tree.ErrorNode;
import org.antlr.v4.runtime.tree.ParseTree;
import org.antlr.v4.runtime.tree.RuleNode;
import org.antlr.v4.runtime.tree.TerminalNode;

import java.util.ArrayList;
import java.util.List;

public class QuestionAnswerConcreteVisitor  implements QuestionAnswerVisitor<List<Question>> {

    @Override
    public List<Question> visitFile(QuestionAnswerParser.FileContext ctx) {
        List<Question> list = new ArrayList<>();
         for(QuestionAnswerParser.QuestionContext c : ctx.question()){
             Question q = new Question();
             q.setTitle(c.getText());
         }
         return  list;
    }

    @Override
    public List<Question> visitQuestion(QuestionAnswerParser.QuestionContext ctx) {
        return null;
    }

    @Override
    public List<Question> visitOption(QuestionAnswerParser.OptionContext ctx) {
        return null;
    }

    @Override
    public List<Question> visitMeta(QuestionAnswerParser.MetaContext ctx) {
        return null;
    }


    @Override
    public List<Question> visit(ParseTree tree) {
       /* List<Question> list = new ArrayList<>();
        for(QuestionAnswerParser.QuestionContext c : tree.accept()){
            Question q = new Question();
            q.setTitle(c.getText());
        }
        return  list;*/

        return null;
    }

    @Override
    public List<Question> visitChildren(RuleNode node) {
        return null;
    }

    @Override
    public List<Question> visitTerminal(TerminalNode node) {
        return null;
    }

    @Override
    public List<Question> visitErrorNode(ErrorNode node) {
        return null;
    }
}


    @PostMapping("/upload")
    public ResponseEntity<?> uploadQuestions(@RequestParam("file") MultipartFile file) {
        try {
            String content = new String(file.getBytes(), StandardCharsets.UTF_8);
            System.out.println("=========="+content+"==========");
            List<Question> questions = qcmService.parseQuestionsFromText(content);
            System.out.println("=========="+questions.size()+"==========");
            return ResponseEntity.ok(questions);
        } catch (IOException e) {
            return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body("File reading error");
        } catch (Exception e) {
            return ResponseEntity.badRequest().body("Invalid file format");
        }
    }

ça m'affiche 0 comme taille

