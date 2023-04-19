
# 02-Les conditions

Pour toutes documentations sur JS 
 https://developer.mozilla.org/fr/docs/Web/JavaScript



## Conditions if : ##

```js
if (true ){
    console.log('Bonjour')
}
```

Permet de vérifier si une condition est vrai ou fausse. 

1er opérateur > ou < à age. 
 
Si on place un >= Supérieur ou =
Idem avec < inférieur ou <= inférieur ou = . 

On a == qui veut dire égale à. 
Mais également === les deux valeurs doivent être identiques. 

```js
'4' == 4 
true
```

il va convertir le string en nombre et comparé. 

Alors que si on fait 

```js
'4' === 4
false
```
Car c'est pas le même type et donc pas la même valeur. 

On éviteras au maximum ==. On préferas === pour plus de sécurité. 

Négation !== on auras donc un résulat n'est pas égale à ... 

Un string vide et = à false idem avec ''== false. 

Une condition est vérifier si elle est truffy.  


## Opérateur logique : 

**Et / OU  && / ||**

Si on met VRAI ET VRAI = VRAI 
VRAI ET FAUX  = FAUX
FAUX ET FAUX = FAUX

OU || :
Dans le cas du ou il faut une seul valeur vrai pour être vrai. 

```js
   const age = 19;
        const pays = 'FR'
      if (
        (pays === 'FR' && age >= 18) || 
      (pays ==='US' && age >= 16)
      ){
    console.log('Vous pouvez conduire.')
```
 Si on trouve cela trop complexe, on peut introduire de nouvelle variable un peu plus simple. 

```js
  const age = 19;
        const pays = 'FR'
        const conduireFrance = pays === 'FR' && age >= 18;
        const conduireUS = pays ==='US' && age >= 16;
        
      if (
        (conduireFrance || conduireUS)
      ){
    console.log('Vous pouvez conduire.')
```

Si on veux afficher un message, si l'utilisateur ne peut pas conduire on vas ajouter un else à notre if. 

```js
 const age = 19;
        const pays = 'FR'
        const conduireFrance = pays === 'FR' && age >= 18;
        const conduireUS = pays ==='US' && age >= 16;

      if (
        (conduireFrance || conduireUS)
      ){
    console.log('Vous pouvez conduire.')
} else{
    console.log('Vous ne pouvez pas conduire.')
}
```

1. if = si 
2. else = sinon 
3. else if = sinon si 

```js
    if(conduireFrance){
        console.log('Vous pouvez conduire en france');
    } else if (conduireUS){
        console.log('Vous pouvez in America');
    } else {
        console.log('Vous ne pouvez pas conduire');
    }
```

C'est comme ceci qu'on pourras écrire des conditions en JS. 


Inversion d'une condition : 

Si on veux inverser un boolean on le feras avec !true ou !false. 

```js
        if(!conduireFrance && !conduireUS){
            console.log('Vous ne pouvez pas conduire');
        }
```

Ex: si on as a || b et qu'on veut faire une inversion : 

!a && !b = différent de a ET différent de b

Voila comment inverser un OU. 

Si on as a && b : 

!a || !b 

## Différent de a OU différent de b

```JS
if(
            !(pays === 'FR' && age >= 18) &&
            !(pays === 'US' && age >= 16)
        ) {
            console.log('Vous ne pouvez pas conduire');
        }
```

Différence, on doit la gérer bloc par bloc : 

```JS  
        if(
            (pays !== 'FR' || age >= 18) &&
            (pays !== 'US' || age >= 16)
        ) {
            console.log('Vous ne pouvez pas conduire');
        }  
```

Vos mieux séparer nos conditions dans des variables, pour gagner en lisibilité. 


Condition sur une varialbe particulière : 


## Le switch case : pour vérifier qu'une varialbe à différente valeur ##

Dans la pratique, c'est assez peut fréquent de l'utiliser. 

```JS
switch(pays){
            case 'FR':
                console.log('Je suis en France')
                break;
            case 'US':
                console.log('Je suis en America !')
                break;    
        }
```

Si on as un pays qu'un ne connais pas on peut alors renseigner une conditions par défaut. Si on es dans aucun des deux cas alors ......

```JS
switch(pays){
            case 'FR':
                console.log('Je suis en France')
                break;
            case 'US':
                console.log('Je suis en America !')
                break;    
            default:
                console.log('Je suis dans un pays inconnus')
                break;
        }
```
On aurait pu également le faire en if, mais le switch permet de gagner du temps. 

Ex: 

On es un service de streaming et on as que 3 films Lilo et Stitch, Matrix, Evil Dead. 

Si l'utilisateur à moins de 13 ans alors go regarder le dessin animé. 

Si l'utilisateur à entre 13 et 16 ans go regarder Matrix. 

Sinon si l'utilisateur à entre 16 et 18 ans go regarder Evil Dead. 


Pour demander l'age de l'utilissateur on vas pouvoir utiliser 'prompt'
```js
prompt('Quel est votre âge')
```
On vas pouvoir sauvegarder le tout dans une varible. 
```js
const age = prompt('Quel est votre âge ?');
```


**Solution :**
```JS
 const age = prompt('Quel est votre âge ?');

        if( age <= 13){
            console.log('Vous devriez regarde Lilo et Stitch');
        }else if (age < 18){
            console.log('Vous devriez regarder Matrix')
        } else {
            console.log('Go regarder Evil Dead bro')
        }
```

**Solution bis :**

```js
const birthyear = prompt('Quel est votre année de naissance ?');
        const year = 2023
        const age = year - birthyear;

        if( age <= 13){
            console.log('Vous devriez regarde Lilo et Stitch');
        }else if (age< 16){
            console.log('Vous devriez regarder Matrix')
        } else {
            console.log('Go regarder Evil Dead bro')
        }
```        


**Autre exo :**

Démontrer que A * B = E est positif/négatif

```js
  const a = prompt('Entrez un premier nombre')
        const b = prompt('Entrez un second nombre')
        const result = a * b;

        if(result > 0){
            console.log(`${a}x{b}=${result} est positif`)
        }else{
            console.log(`${a}x{b}=${result} est négatif`)
        }
```

On peut faire quelques chose comme cela. Mais on veut en écrire le moins possible nous.

```js
const a = prompt('Entrez un premier nombre')
        const b = prompt('Entrez un second nombre')
        const result = a * b;
        let signe

        if(result > 0){
            signe = 'positif'
        }else{
            signe = 'négatif'
        }
```

Avec signe on peut déclarer une variable vide qu'on vas pouvoir modifier à la volet. 
```js
const a = prompt('Entrez un premier nombre')
        const b = prompt('Entrez un second nombre')
        const result = a * b;
        let signe

        if(result > 0){
            signe = 'positif'
        }else{
            signe = 'négatif'
        }
        console.log(`${a}x${b}=${result} est ${signe}`)
```       

Maintenant ajoutant la possibilité de savoir si ce que la personne rentre est un nombre ou pas 
On vas pouvoir tester cela avec "isNan". 
```js
const a = prompt('Entrez un premier nombre')
        const b = prompt('Entrez un second nombre')
        const result = a * b;
        let signe

        if(isNaN(result)){
            console.log(`Rentre un chiffre: ${a}x${b} `)
        }else{
            if (result > 0){
                signe = 'positif'
            } else {
            signe = 'négatif'
            }
            console.log(`${a}x${b}=${result} est ${signe}`)
        }
```       

