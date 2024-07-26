
Démarrer DOCKER DAEMON
Démarrer Dependency Track 

# Backend (maven)

Install in backend
	Générer un fichier SBOM au format CycloneDX dans le répertoire target du projet

`mvn org.cyclonedx:cyclonedx-maven-plugin:makeAggregateBom (ou mvnw)`

Dependency track
Importer manuellement le fichier SBOM  dans Projects/components/uploads BOM




# Frontend avec npm
	 
Installer cycloneDX

`***npm install -g @cyclonedx/bom***`

`npm install --save-dev @cyclonedx/bom`

Générer le fichier SBOM du projet
	
npx @cyclonedx/bom -o bom.xml



# Container

Installer sfty

```shell
curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh -s -- -b /usr/local/bin
```

Génerer l'image le fichier SBOM du conteneur 

syft <nom-image>


