# GitHub Flow

- ⚠️ TODO expliquer, PR, etc... (retrouver mes slides)

## 1ère PR: modifier le test / ⚠️ dans GitHub

⚠️ Montrer que cela crée une branche

- dans l'IHM GitHub
- en modifiant les tests
- montrer ce qu'il se passe en  // dans Jenkins
- ... dans la PR
 => failed
 => aller voir les log de la console

- aller modifier les tests pour les remettre "juste"
- raffraichir si besoin / montrer Jenkins
- maintenant le merge est possible
- merger => il y aura déploiement
- supprimer la branche

### Modifier le README selon le même principe (ou pas)

### Mettre son projet local à jour

```shell
git pull origin master
```

vérifier


## 2ème PR en mode commande: ajouter un service

On va aller ajouter un peu de code et le pousser en production selon le GitHub Flow

### CREER UNE "feature branch"

```shell
git checkout -b feature-babs-service # you named it as you want
# -b -> create new branch
git branch # affiche la branche courante
```

Sur https://github.com/snowcamp2017/snippets

Copier dans votre répertoire local de travail:
- `Component.js`
- `Worker.js`
- `Sensor.js`
- modifier votre fichier `index.js` comme dans `01-index.js`

- ⚠️ Expliquer un peu le code

1. vous pouvez tester sur votre poste:
  - `npm install`
  - `node index.js`

### Maintenant il faut "commiter tout ça"

```shell
git status # vérifier

git add *
git status # voir ce qu'il s'est passé
git commit -m "add a new service 🐰"
git status # vérifier
```

### Maintenant il faut "pousser tout ça"

```shell
git push origin feature-babs-service # ça va créer la branche chez GitHub
```

- si on regarde Jenkins on s'apperçoit la branche est en train d'être testée et déployée
- si vous allez dans votre repository **GitHub**: vous voyez un nouvel affichage/message:
  - qui explique: `Your recently pushed branches:`
  - cliquez sur le bouton `Compare & pull request`
  - décrire tout ce que l'on voit
  - cliquez sur `Create pull request`
- ⚠️ **ne mergez pas tout de suite**
  - Allez modifier quelque chose dans `Sensor.js` par exemple
  ```shell
  git status
  git add Sensor.js
  git status
  git commit -m "🐼 a little change"
  git push origin feature-babs-service
  ```

On peut voir les changements et l'historique dans GitHub
Et donc comme cela on peut continuer à bosser sur sa PR tranquillement

⚠️ COMMENT SYNCHRONISER SA BRANCHE SI MODIF DANS PROJET PRINCIPAL???
=> on le verra dans la partie suivante

- merger si c'est vert
- supprimer la branche (elle est déployée)
- on a mergé sur `master` -> donc déploiement
  - on peut donc vérifier le déploiement et le nouveau service, eg: http://snow-demo-babs.cleverapps.io/sensors/babs-sensor

### On revient sur master

```shell
git checkout master
ls # les fichiers ne sont pas là
git fetch
git merge origin/master
ls
# supprimer la "feature branch" locale
git branch -d feature-babs-service
```

--- si on a du temps
## 3ème avec GitLess

## Parler du client Desktop
