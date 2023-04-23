# Les fonctions 

liens utiles : https://devdocs.io/

Imaginons l'idée d'un petit code "can drive" qui permet à l'utilisateur de savoir si il peut conduire ou non. 

Notre fonction vas avoir besoin de paramètre pour avoir de la logique d'utilisation. Savoir ce qu'elle peut faire ou pas. 

Dans notre cas, on veut que l'application nous renvois un boolean pour savoir si on a le droit de conduire ou pas. 

On vas avoir deux variables "pays" et "age". On vas envoyer ces deux paramètres à notre fonction, et en fonction des paramètres qu'on lui envois elle vas nous retourner un true ou false pour savoir si on peut condurie ou pas. 

## Comment écrire une fonction

Pour cela on vas utiliser le mot clé "fonction" suivis de son nom. 

Puis entre parenthèse on vas lui ajouter des paramètres. 
Ensuite entre { } on vas lui dérouler ce qu'elle doit faire. 

Nomination du nom de la fonction en camelcase. 

```js

function canDrive (age, pays){
        
      }

```

Une fois notre logique implémenter à notre fonction, on vas devoir lui définir ce qu'elle renvois, avec le mot clé return. Dans notre cas on vas vouloir qu'elle nous renvois true ou false. 

```js
  function canDrive (age, pays){
        
        if(
          (age > 18 && pays === 'FR') ||
          (age > 16 && pays === 'US')
        ) {
          return true;
        }
        return false;
      }

```

Une fois notre fonction fini d'être créée, on vas pouvoir l'utiliser en lui ajoutant des paramètres directement entre ( ).



```js
  function canDrive (age, pays){
        
        if(
          (age > 18 && pays === 'FR') ||
          (age > 16 && pays === 'US')
        ) {
          return true;
        }
        return false;
      }

    canDrive(12,'UK')

```

Mais on peut également l'écrire autrement. 

On peut alors créer une constante canDrive et en suite lui dire : 

```js
const canDrive = function  (age, pays){
        
        if(
          (age > 18 && pays === 'FR') ||
          (age > 16 && pays === 'US')
        ) {
          return true;
        }
        return false;
      }
      console.log(canDrive(12,'UK'))
```


Une fonction reste un type d'objet avant tout. On auras des propriétés et des méthodes dessus. 

### Quelle est la différence alors ? 

C'est avant tout une histoire de portée. 

Si on écrit notre fonction sans crééer une constante, alors on peut appeller notre fonction avant d'être créée. 

```js
consol.log(canDrive(17, 'US'))
const canDrive = function  (age, pays){
        
        if(
          (age > 18 && pays === 'FR') ||
          (age > 16 && pays === 'US')
        ) {
          return true;
        }
        return false;
      }
      console.log(canDrive(12,'UK'))
```

Y as cette petite particularité qui est le hosting. Car le JS vas avant tout enregistrer les fonctions avant les constantes. 


### Une fonction peut ne pas retourner ce qu'on lui donne

```JS
function greeting(name) {
      console.log(`Bonjour ${name}`)
     }
     console.log(greeting('Wick'))
```
Cette fonction vas bien nous retourner le nom Wick, mais également undefined. 
Pour la raison qu'elle n'as pas retour. 

Undefined permet de marquer l'absence d'une valeur. 

```JS
     function greeting(name) {
      console.log(`Bonjour ${name}`)
     }
     console.log(greeting('Wick'))
     console.log(greeting('Jhone'))
```

Le premier appel à la fonction prendras le nom Wick et le deuxième appel Jhone. Car elle est undefined. Donc elle peut évoluer. 
La variable est donc dynamique elle vas changer a chaque appel de la fonction. 

Comme pour boucle, les fonctions peuvent appeller des valeurs extérieurs. 

```JS
let i = 0
     function greeting(name) {
      i++
      console.log(`Bonjour ${name}`)
     }
     console.log(i)
     console.log(greeting('Wick'))
     console.log(i)
     console.log(greeting('Jhone'))
     console.log(i)
```

Dans notre exemple, le premier appel de i nous retourneras 0, le second 1 et le troisième 2. On as donc une incrémentation à chaques appel de i. 
La fonction peut donc modifier une variable qui est extérieur à elle. 


Attention cependnant si on commence à vouloir modifier un tableau. Celui ci seras alors modifier pour tout les autres appels qu'on feras. 


```js
 let notes = [15, 12, 14]


     function upNotes (notes) {
      notes[0]++
     }

     upNotes(notes)
     console.log(notes)
```

Si on prends un exemple avec des notes, alors on veras que à chaques appel de la fonction, la notes à l'index zero seras modifiée. 
Pourquoi ? Car nous faisont une modification de l'objet qui vas modifier la variable elle même. 


## Autre notation pour les fonctions. 

### Mot clé 'this'

```js
function maFonction () {
      console.log(this)
     }
     maFonction()
```
Ici on peut voir que this peut être utilisé. This fait appel à une sorte d'objet globale qui es directement disponible dans notre page. 

Quand on appel une fonction, on peut changer la valeur de this. 
On peut appeller notre fonction maFonction.call(/Et lui ajouter nos argument/)

Quand on appel notre fonction on peut lui placer un petit paramètre un peu magique qui seras trouvé dans this. 

```js
 function maFonction () {
      console.log(this)
     }
     maFonction.call(3)
```

Dans certains cas, ça seras super utile. Surtout côté navigateur, car le this pourras faire référence à un bouton qu'on auras cliqué. On peut passer des infos à la fonction. 

Autre exemple si on créée une fonction au niveau d'un objet. 
On pourras alors utiliser this, comme propriété d'un objet. 

```js
 const a = {
        firstname: 'jhon',
        lastname : 'Wick',
        fullname : function () {
          console.log(this)
        }
     }
     a.fullname()
```
Avec le a.fullname() on vas pouvoir appeler notre propriété fullname et pour l'utiliser on ajoute des ( ).

This fera alors référence à l'objet. 
On pourras alors appeller notre fonction lui placer de paramètre tout en ayant l'objet de référence. 

```js

const a = {
        firstname: 'jhon',
        lastname : 'Wick',
        fullname : function () {
          console.log(`${this.firstname} ${this.lastname}`)
        }
     }
     a.fullname()
```

D'ailleurs quand on fait appel à une fonction sur un objet, on appel cela "une methode". 

On as déjà beaucoup de méthode qui éxiste déjà dans JS. 
Exemple la méthode toUpperCase, qui transforme notre texte en majuscule. 


```js
console.log('Hello'.toUpperCase())
```


### Autre notation possible et recommandée 

```js
const maFonction = (param1, param2) => {
        console.log(param1, param2);
      };

      maFonction(1, 2);
```

La principale différence est le comportement de 'this' à l'intérieur. $
Si on veut faire un consol.log de this, alors j'aurais l'objet global. 

Mais si on l'appel avec call  et qu'on lui place un arguement un peu bizarre. 


```js
const maFonction = (param1, param2) => {
        console.log(param1, param2, this);
      };

      maFonction(3, 1, 2);
```

Mais attention,car comme this fait appel a référence à un objet général, nous allons avoir un retoure comme undefined. 

```js
const a = {
        firstname: "jhon",
        lastname: "Wick",
        fullname: () => {
          console.log(`${this.firstname} ${this.lastname}`);
        },
      };
      a.fullname()
```

Contrairement avec le mot clé fonction, les fonctions fléchés ne peuvent pas altéré le this. 
Beaucoup de dev évitent d'utiliser this pour esquiver les problèmes. Dans des fonctions on vas éviter le plus possible. 

Autre avantage des fontions fléchis pouvoir retouner directement. 

```js
const somme = (a, b) => a + b

      console.log(somme(1, 2))
```

Si on se sens à l'aise on peut directement se paser des { }. 