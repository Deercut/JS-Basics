# Les timers

## Introduction

Les timers nous permettent d'afficher quelques choses puis d'attendre un certains moment pour en afficher une autre. 

Ceci est donc une bonne introduction au côté asynchrone de JS. 

## Timer synchrone

On vas créer une fonction qui recevra une durée. L'idée de cete fonction est de nous aider à attendre.

```js 
function wait(duration) {
    
}
console.log('Coucou')
wait(1000)
console.log('Jarrive en delai')

```

Sans rien d'autre le code vas tourner directement. 
On vas pouvoir utiliser des boucles à notre avantages (en évitant l'infinit loop).

### Date.now

On vas utiliser une variable spécial en utiliser la varialbe 'now' sur les Dates. 

Ceci nous donnes le nombre de miliseconde écoulé depuis le 1er Janvier 1970

C'est ce qu'on appel un time stamp, souvent quand on représente les temps en JS ou autre langage on utilise cett donnée là. 

```js 
function wait(duration) {
    const t = Date.now()
    while(Date.now() - t < duration)
}
console.log('Coucou')
wait(1000)
console.log('Jarrive en delai')

```

## L'asynchrone

La démonstration que nous venons de faire est une façon synchrone d'attentes. Mais grâce au JS on vas pouvoir faire du asynchrone, ce qui vas rendre notre code bien plus efficace. 
On as des fonctions interne au JS qui permettent de reproduire ce qu'on as fait masi de façon bien plus efficace. 

### setTimeOut

Comme setTimeOut() par exemple. 
Elle prendras deux paramètres. Une première fonction et le delais (attention il es millisec).

```js 
function wait(duration) {
    const t = Date.now()
    while(Date.now() - t < duration)
}
console.log('Coucou')
// wait(1000)
setTimeOut(()=> {
    console.log('Jarrive en delai')
},1000)
console.log('Jarrive avait le délais')

```

Ici on voit bien que l'asynchrone n'est pas bloquant et ainsi chargé notre log après une seconde. Mais notre setTImeOut vas nous permettre de faire d'autre chose pendant ce temps la. 

### setInterval

Ici nous allons pouvoir reproduir un morceau de code mais avec un intervalle régulier. 

```js 
function wait(duration) {
    const t = Date.now()
    while(Date.now() - t < duration)
}
console.log('Coucou')
// wait(1000)
setInterval(()=> {
    console.log('Jarrive en delai')
},1000)
console.log('Jarrive avait le délais')

```

### ClearInterval ou ClearTimeOut

Ici 'Jarrive en delai' arriveras en boucle toute les secondes.

Nos deux fonctions retournes quelques choses, un entier. 
Pourquoi nous retourner un entier ??
Pour pouvoir rapidement l'identifier ainsi que de le stoper. 

Pour cela on vas voir la fonction "clearInterval" ou "clearTimeOut".
Ainsi avec notre entier on vas le repérer et ensuite avec le clear pouvoir le nettoyer et donc le stopper. 

### Bloquer notre JS

```js 
function wait(duration) {
    const t = Date.now()
    while(Date.now() - t < duration)
}
console.log('Coucou')
// wait(1000)
setTimeOut(()=> {
    console.log('Jarrive en delai')
},1000)

const p = prompt('nom')

```
Ici tant que le prompt ne seras pas fini le js ne vas pas déclancher notre TimeOut. 
Mais dès que le prompt est déclencher le code vas se lancer directement après. 


### Le soucis de l'asynchrone


Le principale problème avec l'asynch et on l'as vue est qu'on vas rapidement devoir imbriquer des call back. 

```js 
function wait(duration) {
    const t = Date.now()
    while(Date.now() - t < duration)
}
console.log('Coucou')
setTimeOut(()=> {
    console.log('Jarrive en delai')

    setTimeOut(() =>{
        console.log('encore moi')
    }, 2000)
},1000)


```

C'est ce qu'on appel le callBack Hell, ou l'enfer des callbacks.

Aujourd'hui on peut résoudre ce soucis avec les promesses. On voit ça peut après. 


# TP 

Afficher 5 fois un message puis faire un décompte. 

```JS 
// Function de chargement d'un message 5 fois. 

let i = 0 
const t = setInterval(() => {
    i++
    console.log('Coucou')
    if( i >= 5){
        clearInterval(t)
        console.log('Je stope')
    }
}, 1000);

// Function de décompte

function decompte (d) {
    console.log(d)
    setInterval(() => {
        n--
        console.log(d)
        if(n === 0 ) {
            clearInterval(d)
        }
    }, 1000)
}

decompte(3)

```
Mais il y as une autre façon de faire, car il peut arriver qu'on oublié de retirer les intervals.

```JS

// Function de décompte

function decompte (d) {
    console.log(d)
    if(d === 0 ){
        return
    }
    setTImeOut(() => {
        decompte(n - 1)
    }, 1000)
}

decompte(3)

```