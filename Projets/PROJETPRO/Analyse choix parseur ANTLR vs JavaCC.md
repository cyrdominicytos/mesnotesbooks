
from docx import Document
from docx.shared import Pt

# Create a new Document
doc = Document()

# Add a title
doc.add_heading('Comparison between ANTLR and JavaCC', level=1)

# Add a table with 3 columns (Aspect, ANTLR, JavaCC)
table = doc.add_table(rows=1, cols=3)
table.style = 'Table Grid'

# Add the header row
hdr_cells = table.rows[0].cells
hdr_cells[0].text = 'Aspect'
hdr_cells[1].text = 'ANTLR'
hdr_cells[2].text = 'JavaCC'

# Add the content rows
content = [
    ("Documentation and Support", 
     "Extensive documentation and large community support.",
     "Well-documented but with a smaller community."),
    
    ("IDE Support", 
     "Plugins available for major IDEs like IntelliJ IDEA and Eclipse.",
     "Less comprehensive IDE support."),
    
    ("Syntax Trees", 
     "Automatically generates Abstract Syntax Trees (AST).",
     "No automatic generation of ASTs."),
    
    ("Debugging Tools", 
     "Provides graphical tools for visualizing syntax trees and parsing errors.",
     "Lacks advanced debugging tools."),
    
    ("Flexibility and Power", 
     "Supports complex grammars with advanced features like semantic actions and contextual grammars.",
     "Simpler to use for basic grammars but less powerful."),
    
    ("Complexity", 
     "Steeper learning curve due to its advanced features.",
     "Easier to learn and use for simple projects."),
    
    ("Performance", 
     "Can be less performant for very simple grammars.",
     "Generally more performant for simple grammars."),
    
    ("Legacy Support", 
     "Newer tool with active development.",
     "Older tool with considerable existing projects and documentation."),
    
    ("Maintenance", 
     "Actively maintained and developed.",
     "Slower development and less active maintenance.")
]

for aspect, antlr_desc, javacc_desc in content:
    row_cells = table.add_row().cells
    row_cells[0].text = aspect
    row_cells[1].text = antlr_desc
    row_cells[2].text = javacc_desc

# Save the document
doc_path = '/mnt/data/ANTLR_vs_JavaCC_Comparison.docx'
doc.save(doc_path)

doc_path
