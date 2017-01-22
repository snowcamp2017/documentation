# "TEAM"

⚠️ ne pas oublier d'ajouter les users à la team

## Cloner l'application things-master et créer une branche

```shell
git clone git@github.com:snowcamp2017/things-master.git
cd things-master
git checkout -b wip-add-buster-service

```

## Modification de `index.js`

Créer un "appel du service" dans `buster-service.js` *et adapter en conséquence*

```javascript
const fetch = require('node-fetch');

module.exports = function(app) {
  app.get('/sensors/buster-sensor', (req, res) => {

    fetch('http://snow-demo-buster.cleverapps.io/sensors/buster-sensor', {
      method: 'GET',
      headers: {
        "Content-Type": "application/json",
      }
    })
    .then(response => response.json())
    .then(jsonData => res.send(jsonData));
  });
}
```


pousser vers le serveur

```shell
git add index.js
git commit -m "add buster service"
git push origin wip-add-buster-service
```

⚠️ Montrer qu'il y a une nouvelle branche dans la liste des branches

## Création de la pull request (sur GitHub)

- aller sur https://github.com/snowcamp2017/things-master
- cliquer sur `Compare & pull request`
- commentez votre PR en notifiant l'équipe
- create pull request

⚠️ **Mais on ne merge pas**
⚠️ Montrer qu'il y a des PR en cours

## Continuer à bosser

### Modifier `index.js`

```javascript
require('./k33g-service')(app)
```

### Créer un composant d'affichage (tag)

Créer un composant `public/buster-service.html`

```html
<buster-service class="ui container segment" style="font-size:16px">

  <h4 class="ui header">{id} | {kind}</h4>
  <p>
    <small class="ui blue label">value: {value} {unit}</small>
  </p>

  <script>
    getInformationService() {
      fetch('/sensors/buster-sensor', {
        method: 'GET',
        headers: {
          "Content-Type": "application/json",
        }
      })
      .then(response => response.json())
      .then(jsonData => {
        this.id = jsonData.id;
        this.kind = jsonData.kind;
        this.value = jsonData.value;
        this.unit = jsonData.unit;

        this.update();
      });
    }
    this.getInformationService();

    const timer = setInterval(this.getInformationService, 2000);

  </script>
</buster-service>
```

### Déclarer le composant + monter le composant

Référencer le composant (dans `public/index.html`):

```html
<script type="riot/tag" src="buster-service.html"></script>
```

Ajouter le composant (dans `public/index.html`):

```html
  <div class="ui container">
    <padding-top></padding-top>
    <application-content></application-content>
    <!-- services -->
    <buster-service></buster-service>
  </div>
```

Monter le composant (dans `public/index.html`):

```html
  <script>
    riot.mount('application-header')
    riot.mount('padding-top')
    riot.mount('application-content')

    // mount services tag
    riot.mount('buster-service')

  </script>
```

## Mettre à jour la PR

```shell
git add *
git commit -m "add buster component"
git push origin wip-add-buster-service
```

⚠️ montrer la PR de mon côté pour montrer qu'elle se met à jour

## Et maintenant on merge !!!!

Donc dans l'interface GitHub

Certains vont avoir des conflits

2 solutions pour gérer:

- mode command line
- web editor

## Mettre à jour son repository

```shell
git checkout master
git fetch
git merge origin/master
# supprimer la "feature branch" locale
git branch -d wip-add-buster-service
```

## Remarque: synchronyser sa feature branch avec master


```shell
git checkout master
git pull
git checkout my-feature-branch
git merge master
```


> infos
> http://things-master.cleverapps.io/
> http://snow-demo-k33g.cleverapps.io/sensors/k33g-sensor
> http://snow-demo-babs.cleverapps.io/sensors/babs-sensor
> http://snow-demo-buster.cleverapps.io/sensors/buster-sensor

> https://github.com/snowcamp2017
> http://jenkins-snowcamp.cleverapps.io/jenkins/job/snowcamp2017
