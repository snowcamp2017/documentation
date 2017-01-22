# :octocat: workshop

## Pré-requis

- avoir un compte GitHub
- je dois inviter chaque user dans la team (et l'orga?)

## Organisation

- https://github.com/snowcamp2017

## Team

- https://github.com/orgs/snowcamp2017/teams/bigfoots
- ⚠️ TODO: inviter chaque participant dans la team `bigfoots`

## Projets

Chaque utilisateur (devra être dans la team) va cloner le projet demo sous un autre nom

```
git clone git@github.com:snowcamp2017/demo.git demo000
cd demo000
git remote set-url origin git@github.com:snowcamp2017/demo000.git
# check
git remote -v
# creer un repo demo000 dans l'organisation snowcamp2017 "nu"
# puis
git push -u origin master
```

```
git clone https://github.com/snowcamp2017/demo.git demo000
cd demo000
git remote set-url origin https://github.com/snowcamp2017/demo000.git
# check
git remote -v
# creer un repo demo000 dans l'organisation snowcamp2017 "nu"
# puis
git push -u origin master
```

## connecter à Jenkins

- du coup faut avoir les users
- paramétrer?
- jenkins file
- ...

### Création utilisateurs

- http://my.jenkins.cleverapps.io/jenkins/securityRealm/
- fait par moi

### Chaque user doit se créer un token GitHub

- aller: https://github.com/settings/profile
- personal access token: https://github.com/settings/tokens
- cliquer sur: Generate new token:
- Token description: jenkins-token
- Scope: repo
- cliquer sur: Generate token
- copier le token dans un coin: 23401f86d4b3f30957002f18cd4d8266c37ca6e3

### Dans Jenkins

- new job: http://my.jenkins.cleverapps.io/jenkins/view/all/newJob
- nommez le "demo000-pipeline"
- choisir "pipeline"
- ok
- check GitHub project -> + url du repo eg: https://github.com/snowcamp2017/demo000/
- check GitHub hook trigger for GITScm polling
- Section Pipeline:
  - "Pipeline script from SCM"
  - Repository URL: ⚠️ ne pas oublier le `.git` à la fin
  - ajouter credential: user + le token en password
  - dans Branches to build -> mettre à blanc

### Dans GitHub via l'IHM

- Ajouter le Jenkinsfile
    ```

    ```
- ensuite aller dans les integrations(de votre repo) (eg: https://github.com/snowcamp2017/demo000/settings/installations)
  - cliquez sur "Add Service"
  - cherchez et sélectionnez "Jenkins (GitHub plugin)"
  - dans "Jenkins hook url": http://my.jenkins.cleverapps.io/jenkins/github-webhook/

### Aller faire une modification sur master directement dans l'IHM

1. par exemple: renommer le nom du projet dans le README.md
2. aller faire planter le test
   -> montrer que le test failed dans la console Jenkins

tout sur master

-> ensuite on explique que c'est pas bien



## Exercice GitHub Flow / Feature Flow

🚧

-> expliquer le flow / la PR

-> proteger les branches pour les PR -> l'avantage c'est que l'on aura le status du build
-> faire PR
-> tout dans l'IHM

puis ensuite en mode commande

## connecter à Clever - pour montrer le deploiement (sur master)

- creer autant d'application que de repo clones


## API Github

## Hubot

Essayer de hoster un rocketchat ou autre chose ?
ou directement sur Facebook ?

## CI home made les bases
✅🕺



## tests - sandbox

### busterbunny69

```
./_DEV_/run buster 9090
git config --global user.name busterbunny69
git config --global user.email buster.bunny.69@gmail.com
git clone https://github.com/snowcamp2017/demo.git demo000
cd demo000
git remote set-url origin https://github.com/snowcamp2017/demo000.git
# check
git remote -v
# creer un repo demo000 dans l'organisation snowcamp2017 "nu"
# puis
git push -u origin master

Username for 'https://github.com': busterbunny69
Password for 'https://busterbunny69@github.com':
```

### babsbunny42

```
./_DEV_/run babs 9091
git config --global user.name babsbunny42
git config --global user.email babs.bunny.42@gmail.com
git clone https://github.com/snowcamp2017/demo.git demo001
cd demo001
git remote set-url origin https://github.com/snowcamp2017/demo001.git
# check
git remote -v
# creer un repo demo001 dans l'organisation snowcamp2017 "nu"
# puis
git push -u origin master

Username for 'https://github.com': babsbunny42
Password for 'https://babsbunny42@github.com':
```



## ressources

- https://guides.github.com/introduction/flow/
