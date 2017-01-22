# Jenkins

## Installation on CC

- ajouter un add-on bucket
- nom du bucket `jenkins-snowcamp`
- relever les infos (id) du bucket

- forker: https://github.com/wey-yu/jenkins-installation dans une orga (snowcamp)

- aller modifier https://github.com/snowcamp2017/jenkins-installation/blob/master/clevercloud/buckets.json

```json
[
   {
      "bucket_host": "bucket-49d33ff3-8e81-4455-9281-2de9006ca051-fsbucket.services.clever-cloud.com",
      "folder": "/jenkins-storage"
   }
]
```

- dans Clever
  - ajouter une application via GitHub (jenkins-installation de l'orga snowcamp2017)
  - selectionner application java war
  - pas besoin de linker (normalement)
- variables d'environnement:
  ```shell
  JAVA_VERSION=8
  JENKINS_HOME=/app/jenkins-storage/.jenkins
  PORT=8080
  ```
- next
- créer un nom de domaine: http://jenkins-snowcamp.cleverapps.io/
- Jenkins sera accessible via http://jenkins-snowcamp.cleverapps.io/jenkins
- passer à une config small
- récupérer le pwd admin dans les logs ou dans le bucket (`/app/jenkins-storage/.jenkins/secrets/initialAdminPassword`)
- copier coller dans l'IHM
- ok
- installer les plugins suggérés

## Paramétrages

⚠️ A refaire pour le workshop, pour montrer
(juste supprimer le job pour le refaire - ou doublonner le job)


### Tools

- aller: Manage Jenkins > Manage Plugins > Available -> search for nodejs
- aller dans `Disponibles` - chercher nodejs
- telecharger
- check `Redemarrer`
- attendre

- Administrer Jenkins > Configuration globale des outils
- Ajouter NodeJS
  - nom: NodeJS-740 (par exemple)
  - check install automatically
  - choisir "installer depuis nodejs.org" et sélectionner l'installeur
  - enregistrer / appliquer

- Administrer Jenkins >  Configurer le système
  - Aller à la rubrique GitHub
  - Ajouter GitHub Server
  - Ajouter Credentials Jenkins
    - choisir "Secret text", le nommer (eg: credentials-4-gh)
    - renseigner le token => expliquer les personal web tokens
  - Selectioner les credentials créees + test connection
  - enregistrer / appliquer

### Job

- créer un nouveau job
- nommer le job: snowcamp2017
- choisir GitHub Organization
- OK

- créer des credentials
  - cette fois ci user - mais avec le tojen à la place du pwd

- enregistrer / appliquer

### GitHub side

#### WebHook -> service

- aller dans les settings de votre projet de demo
- cliquer sur `integrations & services`
- ajouter service Jenkins GitHub plugin
- donner l'url de notre Jenkins
  - http://jenkins-snowcamp.cleverapps.io/jenkins/github-webhook/
- `Add service`

⚠️ Expliquez à quoi cela sert - que va-t-il se passer

#### Jenkins file

- créer dans votre repo de demo un fichier `Jenkinsfile` / 2 façons de le faire
  - avec git
  - dans l'IHM GitHub

```groovy
node {
  stage 'Checkout'
  checkout scm

  stage 'Build'
  def nodeHome = tool name: 'NodeJS-740', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
  env.PATH = "${nodeHome}/bin:${env.PATH}"

  sh "npm install"
  sh "npm test"
}
```

⚠️ Expliquer ce qu'il se passe
⚠️ Montrer le Jenkins qui scan
⚠️ de mon côté lancer le scan

#### Protected branches

- choisir `master`
- check `Protect this branch`
- check `Require status checks to pass before merging `
- check `continuous-integration/jenkins/branch`
- `Save changes`
