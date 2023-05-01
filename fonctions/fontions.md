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
Dans ce ça on crée une fonction qui renvoit cette opération a + b. 

Il es possible de passer des fonctions en paramètres de fonctions.

On vas créer une const isPairt et lui attribuer une fonction.

```js
 const isPair = function (a, fn){
        return a % 2 === 0; 
      }
```

## La fonction callback

Mais on s'imagine qu'on vas lui donner une fonction en paramètre (fn), ce qui veux dire que si le nombre est pair on vas éxécuter cette fonction. 
Et si le nombre n'est pas pair on vas pas l'éxécuter. 

```js
 const isPair = function (a, fn){
        if (a % 2 === 0){
          fn(a)
        } 
      }

      isPair(4, function(n){
        console.log('Mon nombre est paire' + n)
      })
```
Ici nous avons donc un log qui ne s'afficheras uniquement que si le nombre est paire. Si jamais il es impair, alors le log ne s'afficheras pas. 

Ici on vas alors parler de cette fonction présente dans notre fonction une CallBack.

Quand un paramètre est une fonction qu'on vas appeller celon certaines conditions, alors cette fonction est nommée CALLBACK. 
C'est vraiment utile quand on vas placer des fonctions. 

## Exercice 1 :

Faire en sorte que l'utilisateur doivent deviner un nombre. Mais aujourd'hui on peut générer une fonction qui donne un chiffre aléatoire. 

```js

/* 
      On crée un nombre entre 0 et 10 
      3 essais pour deviner le mot
      isRight(n)
      guess()
*/
```

```js

//On crée un nombre random entre 0 et 10

 function getRanDomInt(max){
        return Math.floor(Math.random()* (max + 1))
      }
      const solution = getRanDomInt(10)
      console.log(solution)
//Fonction pour vérifier si on a raison ou pas

      function isRight(n){
        return solution === n 
      }
//Fonction pour entrer un chiffre 

      function guess() {
        const number = prompt('Entrez un chiffre') * 1
        return isRight(number)
      }
//Condition pour valider ou invalider 3 essais

      for (i = 0; i < 3; i++){
        if(guess()){
          console.log("BRAVO")
          break;
        }else if(i === 2){
          console.log("Vous avez perdu...")
        }
      }
```
Avantage de pouvoir faire des fonctions de cette façon, et nous l'avons vue, c'est qu'on peut créer des bouts de code qu'on vas pouvoir ré-utiliser un peu plus tard quand on vas en avoir besoin. 


## Exercice 2 :

```js
/* 
     Passer un nombre,
     Réussir à dire si le nombre est premier ou non. 
     Un nombre uniquement divisible par 1 ou lui même. 
*/
```

```JS

 function isPrim (n){
        if (n < 2){
          return false
        }
        for (let i = n - 1; i > 1; i-- ){
          if(n % i === 0 ){
            return false
          }
        }
        return true;
      }


```



### Earyly Return : 

On vas rapidement mètre un return pour stopper l'éxécution de notre code si jamais celui-ci n'est absolument pas nécessaire. C'est le cas au début de notre code avec : 

```JS
function isPrim (n){
        if (n < 2){
          return false
        }

```



## A retenir : 

Les fonctions ne sont rien de plus qu'un type particulier en JS et on peut les utiliser à n'importe quel endroit. 

Il y as 3 façons d'écrire une fonction : 

```JS

//Méthode 1

//Fonction qui seras écrite avec un paramètre comme ceci et donc seras déclarée de façon global
function isPrim (n) 

//Méthode 2

//Soit dans une constante 

const function isPrime(n){

}

//Méthode 3

//Soit de façon fléché

fullname: () => {
          console.log(`${this.firstname} ${this.lastname}`);
        },


```

## Pratiquer les fonctions


## Le palindrome

Essayons de créer un bout de code avec une fonction qui vas vérifier si le mot renseigner est un palindrome ou pas. 

C'est un exercice assez basique mais qui permet de bien prendre en main les fonctions. 

```js
console.log("Test Palindrome");

      function isPalindrome(word) {
        Split
        const letters = word.split("");

```

Ici nous allons simplement créer une fonction qui prends en paramètre une variable word



### Fonction reverse

Nous allons ensuite faire appel à une fonction qui éxiste déjà dans JS, le split. 
Le split vas nous permettre de découper notre mot lettre par lettre. 

```js
        reverse
        letters.reverse();

```

### Fonction join

La fonction "join" permet de créer et renvois une nouvelle chaine de caractères en concaténant tout les 
éléments d'un tableau. 

```js
        Join
        const reverseWord = letters.join("");
```

### Fonction toUppercase

La fonction toUppercase vas permettre de transformer nos caracètre en MAJUSCULE


```js
        //ToUpperCase
        //return word.toUpperCase() === reverseWord.toUpperCase()
```


### Utilisation des fonctions

Si maintenant on veux utiliser toutes ces fonctions en une ligne on peut le faire ainsi. 


```js
        //All in one or two
        const reverseWord = word.split("").reverse().join("");
        return word.toUpperCase() === reverseWord.toUpperCase();
      }
```




Maintenant metons tout en place correctement en déclarant nos mots et ce qu ils doivent retourner. 

```JS

  const reverseWord = word.split("").reverse().join("");
        return word.toUpperCase() === reverseWord.toUpperCase();
      }
      const words = {
        kayak: true,
        SOS: true,
        Kayak: true,
        Bonjour: false,
      };

//La boucle for vas nous permettre de parcourir tout nos mots. 
      for (let word in words) {
        if (isPalindrome(word) !== words[word]) {
          console.error('isPalindrome(${words})')
        }
      }
```



### Fonction avec tableau d'étudiant


Ici on vas vouloir créer une première fonction qui vas afficher la moyenne d'un tableau de notes d'étudiant. 

```JS

const students = [
        {
          name: "Jean",
          notes: [1, 20, 19, 16, 12],
        },
        {
          name: "Mary",
          notes: [14, 6, 15, 20, 15],
        },
        {
          name: "Dustin",
          notes: [12, 2, 14, 10, 8],
        },
        {
          name: "Axel",
          notes: [1, 20, 10, 16, 12],
        },
        {
          name: "Chloe",
          notes: [1, 20, 19, 16, 12],
        },
      ];

```
Voila notre tableau d'étudiant avec des notes pour chaques étudiants. 

## Moyenne des notes 

Nous allons créer une fonction qui vas nous renvoyer une moyenne de toutes nos notes puis on vas afficher le résultat. 


```JS
 const moyenne = (notes) => {
        let sum = 0;
        for (let note of notes) {
          sum = sum + note;
        }
        return sum / notes.length;
      };
```

Ensuite nous allons ajouter la valeur trouver à nos tableaux de notes. 

```jS
const compareStudent = (a, b) => {
        return b.moyenne - a.moyenne;
      };
```

Nous allons pouvoir ensuite organiser nos moyennes et également trouver la note Max et la note Minimal de chaques étudiants. 
Pour cela on vas utiliser deux fonctions qui éxistent déjà dans Javascript, Math.min et Math.max


```js
for (let student of students) {
        //Ici on modifie un objet et donc tout ce qui feras
        //référance à notre objet
        student.moyenne = moyenne(student.notes);
        student.worst = Math.min(...student.notes);
        student.best = Math.max(...student.notes);
      }
```

### Fonction sort

Maintenant on vas utiliser la fonction javascript "sort". Sort nous permet d'organiser les éléments en place, soit de façon 
alphabétique ou d'une façon définis. 

```js
students.sort(compareStudent);
```

Maintenant qu'on a tout cela, on vas vouloir organiser un peu plus nos informations. 
Pour cela on vas créer une nouvelle fonction "formatStudent" qui vas formater les informations sorties. 

```js
const formatStudent = (student) => {
        return ` ${student.name} avec une moyenne de ${student.moyenne}, 
        meilleur note (${student.best}),
         pire note (${student.worst})`
      }
```

### Faire un top 3 des meilleurs élèves

Pour cela on vas devoir allez parcourir nos tableaux et trouver celui qui se trouve en position 1, 2 et 3. C'est un top 3 après tout. 

Pour ça, on vas allez parcourir nos tableaux et pour RAPPEL la première position dans un tableau est à la position 0 

```js
console.log(`TOp 3 étudiant
      1 : ${formatStudent(students[0])}
      2 : ${formatStudent(students[1])}
      3 : ${formatStudent(students[2])}
      `);
```      


## Fréquence de mot dans une string

Ici on vas vouloir trouver combien de fois un mot est présent. 

Pour ça on vas devoir créer un objet avec "mot" en propriété et retirer les caractère spéciaux. 
Découper tout les mots avec une fonction "split". Créer un objet qui contient les fréquences.

```js
      const phrase = 'Vous, vous, savez pas!? Vous vous vous pas, y as Pas, de pas, Bonne ou mauvaise ...'
      const frequencies = {}
```

Ensuite on vas faire un tableau ignored, dans lequel on vas y renseigner tout les caracètres à retirer. 

```js
 const ignored = [',','!','?']
       let cleanPhrase = phrase.toLowerCase()
        for (let charactère of ignored){
          cleanPhrase = cleanPhrase.
          replaceAll(charactère, '')
        }
```

### Le split

Ensuite on vas créer un écartement avec la fonction .split(' '), qui prendras en paramètre du vide dans notre cas. 

```js
const words = phrase.split(' ')   
```

Ensuite on vas pouvoir boucler sur chaques mots présents avec une boucle for mais qui auras certaines conditions. 

On vas lui demander de boucler unqiuement si la taille de notre mots est supérieure ou égale à 4 et que le mot n'est pas vide. 
Frequencies est un array qui seras définis juste après. 

```JS
for (let word of words){
        if (word !== ' ' && word.length >= 4){
          if (frequencies[word]){
          frequencies[word]++
          } else {
          frequencies[word] = 1
         }
        }
       }
```

Frequencies est donc un array (tableau) qui vas stocker la fréquences d'apparitions d'un mot. 


On vas également lui demandé de chercher la clé avec la lettre "k". C'est une convenance que la clé/key seras toujours noté K.

```js
       const frequenciesArray = []
       for (let k in frequencies){
        frequenciesArray.push({
          word : k,
          count : frequencies[k]
        })
       }
```
Enfin on vas avoir besoin d'une fonction de comparaison pour pouvoir comparer les nos words. Pour ça on vas refaire appel à notre fonction "sort" de l'exemple précédent. 

```js
requenciesArray.sort((a, b) => b.count - a.count)
       console.log(`Les mots les plus fréquent sont  "${frequenciesArray[0].word}", "${frequenciesArray[1].word}", "${frequenciesArray[2].word}"`)
```