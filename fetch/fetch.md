# `Appel HTTP avec Fetch.`

## `A quoi ça sert donc ?`

Fetch est une méthode très importante, pour pouvoir faire des requêtes HTTP depuis le JS si on fait ça côté browser, c'est le navigateur qui feras l'appel si on fait ça côté server et bien ce seras lui qui feras l'appel. 

### `JSONPLACEHOLDER pour tester.`

Il s'agit d'un site qui fournis des petites API pour pouvoir faire des testes rapidements.

### `Implémentation d'une requête.`


```js 

    const r = fetch('https://jsonplaceholder.typicode.com/users')

    console.log(r)
```
C'est assez rapide à faire une requête. 

Fetch est une fonction qui utilise les promesses. Dans notre consol on vas voir "promesse" c'est elle qui vas nous afficher nos data.

On peut donc utiliser un then pour voir notre promess.

```js 

    fetch('https://jsonplaceholder.typicode.com/users')
    .then(r => console.log(r))

```

Nous ce qu'on voudrais maintenant c'est récupérer le contenu de la réponse.

### `.text()`

Pour ça on vas utiliser une fonction text qui vous nous permettres d'avoir une représentation textuelle des data de notre API. 

```js 

    fetch('https://jsonplaceholder.typicode.com/users')
    .then(r => re.text())
    .then( body => console.log(body))

```

### `.json()`

Autre fonction, celle ci nous retourne nos data dans la console sous une structure JSON avec array object et autre. 

```js 

    fetch('https://jsonplaceholder.typicode.com/users')
    .then(r => re.json())
    .then( body => console.log(body))

```

### Méthode fetch avec error hanlder.

L'idée ici est de créer une méthode asynchrone qui vas nous retourner nos data seulement si il n'y as pas d'erreur dans l'appel fetch qu'on veut faire. 


```js

async function fetchUser () {
    const r = await fecth('https://jsonplaceholder.typicode.com/users')
    if( r.ok === true ) {
        return r.json()
    }
    throw new Error('Bas ça marche pô, à tout cassé.')
}

fetchUser().then(user => console.log(users))

```

Si on veut pouvoir faire une requête vraiment propre, on vas devoir ajouter un en tête à notre requête. Pour ça on vas utiliser `headers`

Le headers vas nous permettres de signaler qu'à cette instant on attends du JSON. 


```js

async function fetchUser () {
    const r = await fecth('https://jsonplaceholder.typicode.com/users')
    methode: 'GET',
    headers: {
         "Accept": "Application/JSON"
    }

    if( r.ok === true ) {
        return r.json()
    }
    throw new Error('Bas ça marche pô, à tout cassé.')
}

fetchUser().then(user => console.log(users))

```
Autres propriétées, `méthode`. On peut définir si la méthode qu'on veut passer est une méthode GET, POST.

### `Envois de données.`

Imaginons qu'on veuille envoyer des données à un server, dans le cadre d'un remplissage de formulaire. 

Pour le coup on vas devoir utiliser la méthode 'POST' et changer notre appel à l'API


```js

async function fetchUser () {
    const r = await fecth('https://jsonplaceholder.typicode.com/posts'{
        methode: 'POST',
        headers: {
         "Accept": "application/json"
         // Ici on ajoute le type de contenu qu'on vas envoyer.
         "Content-type": "application/json
        },
    body: JSON.stringify({title: 'Mon premier titre'})
    //stringify vas nous permettre de changer notre Json en un string.
    })
    if( r.ok === true ) {
        return r.json()
    }
    throw new Error('Bas ça marche pô, à tout cassé.')
}

fetchUser().then(user => console.log(users))

```

### `Arrêter un fetch`

Ici nous voulons stopper l'action de fetch dès qu'on reçoit la première requète.
De base on devrait recenoir nos post après nos users.

Pour ça on vas pouvoir utiliser une promese et récupérer son résultat déjà. 

```js

Promise.race([
    fecth('https://jsonplaceholder.typicode.com/posts/?_limit=5&_delay=2000')
    fecth('https://jsonplaceholder.typicode.com/users/?_limit=5')
]).then(r => r.json()).then(console.log)

```
Le seul soucis c'est qu'ici même si on stop à la première requête qu'on reçoit, l'autre requête vas quand même ce faire, on peut le voir dans l'onglet réseau. 

Il faudrait annuler notre requête. `Attention c'est bizarre.`
Il vas falloir ajouter une fonction : AbortController c'est un controler qui vas abort nos requête HTTP. 

Puis après notre fetch on vas pouvoir passer une seconde option `signal`. 
Ceci nous permettra d'envoyer un signal d'annulation. 

Puis il faudras enfin annuler nos requete via ce signal.

```js

const a = new AbordController()
Promise.race([
    fecth('https://jsonplaceholder.typicode.com/posts/?_limit=5&_delay=2000', {
        signal: a.signal
    }),
    fecth('https://jsonplaceholder.typicode.com/users/?_limit=5', {
        signal: a.signal
    })
]).then(r => r.json()).then(body => {
    a.abort()
    console.log(body)
})

```