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


## Asynch function


Deux façons de créer une fonction asynchrone : 

```JS

async function main(){

}

```

```JS

const main = async () => {

}

```
Exemple concret : 

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

asynch function main() {
    return 4
}

console.log(main())
// Ici on retourne une promess directement géré.



wait(2000)
    .then(() => {
        console.log('Attente 2s')
        return wait(1000)
    })
    .then(() => {
        console.log('Attente 1s')
    })

```

### Le await dans une fonction asynchrone.

Si on veut re attendre 2 secondes et afficher un message d'erreur ensuite on vas pouvoir utiliser await puis ajouter une promesse dont on attends la résolution.

```JS

async function attend(){
    await wait(2000)
    console.log('Hello world')
    await wait(1000)
    console.log('Bonjour le monde')
}

```

On voit donc que c'est bien plus simple et compréhensible que le système de callback classique.

Si on veut tester un fail, il vas alors falloir capturer l'erreur avec un try catch classique.

```JS

async function attend(){

   try {
    await waitAndFail(2000)
    console.log('Hello world')
    await wait(1000)
    console.log('Bonjour le monde')} catch(e){
        console.log('Error', e)
    }
}

```

Si jamais notre promess retourne un résultat on peut l'utiliser avec le await.

```JS

async function main(){
    const duration = await wait(2000)
    console.log(`Duration: ${duration}`)
}

main()
    .then(n => console.log)

```

Suivis certains environement on peut utiliser aussi "top level await"
Ce qui veut dire que si on utilise un await il doit être dans une fonction asynchrone OBLIGATOIREMENT !!! 


## Combinaison de promesse

Promise.resolve & Promise.reject permette tout simplement de retourner ou des algo retournes des promises à la place d'objets classique.

### Promise.all()

On vas lui passer un premier paramètre un itérable (comme un tableau)

On auras en retour une nouvelle ormesse qui auras comme résultat la résolution de toutes les promesses.

Si une des promesses dans la liste échoue alors ça nous retourneras l'erreur de la promesse en questions.

```JS
Promise.all([waitAndFail(1000), wait(2000)])
    .then(console.log)
    .catch(console.log)

    // On s'attends à n'avoir que 1000 dans la console.
    // La promess échoue et le catch seras directement appellé et retourneras le résulat de la première promesse qui auras échoué.

```
### Promise.allSettled()

Un peu le même principe que le all sauf que ça vas ignorer les promesses qui vont échouer.


```JS
 Promise.allSettled([wait(1000), wait(2000)])
    .then(console.log)
    .catch(console.log)

```

On auras en retour 2 mais on auras également deux tableaux qui aurons chacun des objets qui nous retournerons le log de nos 2 promises.

Si jamais on as une promises qui échoue, on auras toujours le log de 2 qui serais retourné, mais le tableau nous présenterais alors 2 objets, un avec un fail et l'autre avec un fullyfield.


### any()

La méthode any() prends en paramètre plusieurs promesses, any vas retourner le résultat de la première promises qui est résolut. 

Si jamais la promesse échoue alors any vas nous retourner la première promesse qui n'est pas rejeté dans notre tableau de promesse.

Si jamais toutes les promesses échoues, dans ce cas on auras un message d'erreur "Aggregate Error".


### race()

Un peu similaire au any(). Sauf que si la première promesse échoue alors, il vas concidérer que c'est un echec. 

Il vas regarder la promesse à terme. Si elle est tenue alors il vas le retourner. 

Si jamais elle n'est pas tenu alors il vas retourner la promesse la plus rapide et l'afficher via le catch.


## Ensuite ? 


Il faut bien comprendre quand on crée une promesse, le code inscrit dedans est directement éxécuter. Ce n'est pas le .then qui vas lancer le code.

L'utilisation du asynch est nécessaire uniquement si j'ai un await à l'intérieur. Ce n'est pas nécessaire si jamais on retourne directement une promesse.

