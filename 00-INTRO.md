# Intro

## Objectifs

Expliquer tout ce que l'on va faire


une app qui centralise tout ça

## Pré-requis

- avoir un compte GitHub + github parametré
- je dois inviter chaque user dans la team (et l'orga?) ⚠️
- avoir nodejs
- Eventuellement vous pouvez preparer à l'avance avec mon dockerfile

```shell
git config --global user.name busterbunny69
git config --global user.email buster.bunny.69@gmail.com
# Generating a new SSH key and adding it to the ssh-agent
# https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/
ssh-keygen -t rsa -b 4096 -C "buster.bunny.69@gmail.com"
eval "$(ssh-agent -s)"
```
- https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/
- copier le contenu de ` ~/.ssh/id_rsa.pub` dans GitHub
  - `cat ~/.ssh/id_rsa.pub`
  - https://github.com/settings/keys

### Organisation

- https://github.com/snowcamp2017

### Team

- https://github.com/orgs/snowcamp2017/teams/bigfoots
- ⚠️ TODO: inviter chaque participant dans la team `bigfoots`

## Etape 01 - creation du repository

Chaque utilisateur (devra être dans la team) va cloner le projet demo sous un autre nom

### Creer un repo sur GitHub dans l'organisation snowcamp2017

- allez sur le site GitHub
- https://github.com/organizations/snowcamp2017/repositories/new
- `demo-buster` (donc `demo-<handle>` par exemple)
- public
- ne pas initialiser de README, ni rien d'autre

### Dans la console, cloner le projet de demo

```shell
git clone git@github.com:snowcamp2017/demo.git demo-buster
cd demo-buster
git remote set-url origin git@github.com:snowcamp2017/demo-buster.git
# check
git remote -v
# puis pour pousser ça chez GitHub
git push -u origin master
```

Aller vérifier https://github.com/snowcamp2017/demo-buster (avec le bon nom de répertoire)

## Hébergement (cc)

- inviter sur cc les participants dans l'orga snowcamp2017
- aller dans `Members`
- ajouter `buster.bunny.69@gmail.com` (par ex) comme membre avec un rôle dev
- relever ses mail et joindre l'organisation
- s'authentifier avec son handle GitHub par ex et creer son compte

=> bien vérifier que l'on bosse / est positionné sur l'orga

### Creer une application:

- add an application
- chercher son repo github (`snow-demo-buster` dans l'exemple)
- choisir une app de type **NodeJS**
- changer la taille (pico) ... ou pas
- create
- pas d'addon
- on ne change pas le port
- ajouter un nom de domaine (eg: http://snow-demo-buster.cleverapps.io/)

#### Montrer ...

- les parametres de la branche pour le déploiement:

Pour vérifier que tout fonctionne:

- aller sur http://snow-demo-buster.cleverapps.io
- et sur http://snow-demo-buster.cleverapps.io/hello/world


## Changer le code

### dans le terminal / la console

Aller modifier le service par exemple:

```javascript
app.get('/hello/world', (req, res) => {
  res.send({
    message: "Hello 🌏!",
    whoami: "buster"
  })
});
```

- commiter les modifs
- envoyer chez GitHub (pushing changes)

```shell
git add index.js
git commit -m "service update 😛"
git push origin master
```

- aller vérifier chez GitHub
- on s'aperçoit que le déploiment s'effectue aussi
- aller verifier son service

### dans l'IHM GitHub

Faire la même chose


## Sites sympa pour Git

- http://rogerdudler.github.io/git-guide/
- http://dont-be-afraid-to-commit.readthedocs.io/en/latest/
