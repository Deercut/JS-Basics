# Les Promises

## Le pourquoi ? 

Le principale soucis de l'asyn est qu'on peut vite se retrouver à écrire des callsback dans des callbacks et se retrouver dans l'enfer des callsbacks 

Dans le JS on es des objets qui vont nous permettrent de gérer ce côté asynch pour pouvoir travailler plus facilement. 

Ces objets les promesses.

## Utilisation 

Pour les utilier on vas avoir d'une nouvelle instance de l'objet promes.

Au niveau de son constructeur les promess attentes deux paramètre.

Un premier "resolve" et "reject".



```JS

const p = new Promise([resolve, reject] =>{
    resolve(4)
    console.log(p)
})
// Ici on as une promesse qui se résout tout de suite.

```

#### Réolve

Résolve est employé pour définir quand la promesse est tenu. 


#### Reject 

Reject est utilisé pour signaler que la promess n'est pas remplis.

Le console.log(p) nous permet d'en apprendre plus sur cette promesse. 

En effet on auras comme retour {fulfilled: 4}

Si au lieu d'utiliser resolve on utilisais "reject" on aurais alors comme réponse de notre log
{rejcted: 4}

### Résolus ou pas ?!

Au final c'est surtout ça qui nous intéresse, savoir si la promess et passé ou pas. 

Pour ça on vas avoir deux méthodes pour tester le résultat de notre promess


#### Then

Then est une méthode qui prends en paramètre une callbacks qu'on vas appeller. Ce callback prendras en param les valeurs retournées lors de la résolution de la promess.

```JS

const p = new Promise([resolve, reject] =>{
    resolve(4)
    
})
p.then((n)=>{
    console.log('Le nombre', n)
})

// n retourneras 4

```

Si jamais la promess échue on peut capturer cette échec avec la méthode catch. 

```JS

const p = new Promise([resolve, reject] =>{
    reject(4)
    
})
p.catch((e)=>{
    console.log('Eche', e)
})

// n retourneras 4

```

On vas pouvoir enchainer le then et le catch de la façon suivante. 

```JS

const p = new Promise((resolve, reject) => {
    resolve(3)
})
p.then((n)=>{
    console.log('Le nombre', n)
}).catch((e)=>{
    console.log('Erreur,' e)
})

```

Si la promess fonctionne alors n seras retourné sinon e seras retourné.


## Ok mais du coup les callbacks ?

Avantage est que tout ce qu'on utilise dans le then ou le catch peut être re utilisés

Du coup on vas pouvoir gérer un peu plus facilement la compréhension et l'indentation de notre code. 


```JS

const p = new Promise((resolve, reject) => {
    resolve(3)
})

p.then((n)=>{
    console.log('Le nombre', n)
    return 4
})
.then((n)=> console.log('Le nombre 2', n))
.catch((e)=>{
    console.log('Erreur,' e)
})

```

Si jamais on ne métait pas de return alors le log nous retournerais undefined. Le then serais quand même exécuter mais il ne retournerais rien.

```JS

const p = new Promise((resolve, reject) => {
    resolve(3)
})

p.then((n)=>{
    console.log('Le nombre', n)
    throw new Error('echec')
})
.then((n)=> console.log('Le nombre 2', n))
.catch((e)=>{
    console.log('Erreur,' e)
    return 2
})

```

Ici on vas pouvoir catcher la 1er erreur et avoir le reste du code qui vas quand même tourner. 

On as tjs des callbacks, mais on vas pouvoir représenter du code sequencielle bien plus rapidement.


### Finaly 3ème méthode qu'on peut call sur les promesses.

Finaly est quelque chose qui seras exécuté peut importe si la promess est validé ou pas. 

## Promess qui réussi et échoue

```Js

const p = new Promise((resolve, reject)=>{
    resolve(4)
})

function wait(duration){
    return new Promise((resolve, reject)=>{
        setTimeout(()=>{
            resolve(duration)
        }, duration)
    })
}

function waitAndFail(duration) {
    return new Promise((resolve, reject)=>{
        setTimeOut(()=>{
            reject(duration)
        }, duration)
    })
}

// On vas re tester notre promes

wait(2000)
    .then(() => {
        console.log('Attente 2s')
        return wait(1000)
    })
    .then(() => {
        console.log('Attente 1s')
    })

```
Le fait de pouvoir appeller à la suite permet d'éviter le callback hell et du coup on auras un seul et unique niveau de callback.


### Asynch


Deux façons de créer une fonction asynchrone : 

```JS

async function main(){

}

```

```JS

const main = async () => {
    
}

```

```JS


function wait(duration){
    return new Promise((resolve, reject)=>{
        setTimeout(()=>{
            resolve(duration)
        }, duration)
    })
}

function waitAndFail(duration) {
    return new Promise((resolve, reject)=>{
        setTimeOut(()=>{
            reject(duration)
        }, duration)
    })
}




wait(2000)
    .then(() => {
        console.log('Attente 2s')
        return wait(1000)
    })
    .then(() => {
        console.log('Attente 1s')
    })

```