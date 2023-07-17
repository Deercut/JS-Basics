# Les classes et programmation orienté objet (POO) et prototype

Quand on crée un objet simple avec une propriété, et qu'on ajoute un .

On vas voir qu'il y as déjà pas mal de propositions. Ceci est du au phénomène de prototype.

Quand on cherche à accéder à une propriété ou une méthode il vas dabords chercher dans l'objet et si il ne trouve pas, il vas chercher dans le prototype.

On vas pouvoir y accéder également en faisant

```js

Oject.getProrotypeOf("notre variable")

```

Si on fait un getPrototypeOf d'un string, 
on vas avoir l'info que c'est un string et on vas avoir alors toutes les méthodes qui lui sont rattachées. 

Une chaine de caractère a donc ses propres méthodes ensuite elle a un prototype qui contient des méthodes particulière. Ce prototype auras lui même les méthodes de l'objet. 

```js
str >> String.prototype >> Object.prototype
```
Mais de base on vas pouvoir directement allez chercher nos méthodes en faisant un Object. et on vas avoir des exemples de méthodes. 

On iras rarement à ce niveau. 

### Est ce qu'on peut créer nos prototypes ?

Lister tout un tas de méthode pour pouvoir créer des objets bien plus rapidement. 

Si on veut représenter un éléve avec nom prénom avoir une méthode qui permet d'afficher le nom et prénom tout attachés, on pourras le faire avec les classes. 

# Syntaxe des classes


```js
class Student {

}
```
Rien que avec ça, on viens de créer notre première classe personnalisée. 
Si par curiosité on veux regarder le type de Student.

```js
typeof Student
```
On vas alors nous dire que c'est une fonction

Les prototypes sont des fonctions. 

### Donner des propriétées

```js
class Student {
        ecole = 'Jules Ferry'
}
```

Si maintenant on veux créer un nouvel étudiant mais qui es dans l'école Jules Ferry. 

On feras alors la création d'un étudient = new (notre classe).

```js
class Student {
        ecole = 'Jules Ferry'
}
const john = new Student()
console.log(john)
```
On vas alors voir notre objet Student et voir qu'il a de suite la propriété ecole. 

## Construire notre élève avec le constructor 

Avantage avec les fonctions qui sont définis dans les classes n'ont pas besoin du mot clé fonction devant. 

```js
class Student {
        ecole = 'Jules Ferry'


        constructor(firstname, lastname) {
 
        }
      }
```
On a donc dit que le constructor devait avoir 2 paramètres nom et prénom

Quand on vas initialiser notre étudient 
"const john = new Student()"
On vas devoir ajouter nos paramètres également dans Student. 
Exemple : John et Doe

```js
class Student {
        ecole = 'Jules Ferry'
        constructor(firstname, lastname) {
        this.firstname = firstname
        this.lastname = lastname
        }
      }
      const john = new Student('John', 'Doe')
```

Maintenant on vas pouvoir définir des propriétés dans notre objets avec "this" qui permettra d'accéder à l'objet. 

Du coup on vas avoir 3 propriétés : 

ecole (déjà mise dans la classe)

firstname : ajouté par nous même.

lastname : ajouté par nous même. 

```js
 class Student {
        ecole = 'Jules Ferry'
        constructor(firstname, lastname) {
          this.firstname = firstname
          this.lastname = lastname
        }
      }
      const john = new Student('John', 'Doe')
      const chloe = new Student('Chloé', 'Papin')
      console.log(john, chloe)
```
Ici on vas donc pouvoir créer à la volé de nouveau étudiant. 


## Et si on ajoutait des notes ?

Si on voulait ajouter des notes, mais pas directement dans le constructor ? 

On vas donc devoir se faire une méthode qui permettra de renseigner les notes, mais uniquement pour jhon par exemple ?? 

```jS
const john = new Student('John', 'Doe')
      const chloe = new Student('Chloé', 'Papin')
      john.setNotes([10, 12, 9])
      console.log(john, chloe)
```
Ainsi seul Jhon auras des notes d'insrcit et pas Chloé. 

Ainsi nos objet sont remplis avec des notes en plus. 

Maintenant imaginons qu'on veuille ajouter une méthode pour savoir si la personnes peut passer ou pas en classe supérieur ?

On vas pouvoir retrouver notre ancien fonction de moyenne et l'utiliser ici :

```js
const moyenne = (notes) => {
        let sum = 0 
        for (let note of notes){
          sum = sum + note
        }
        return sum / notes.lenght
      }
      
      class Student {
        ecole = 'Jules Ferry'


        constructor(firstname, lastname) {
          this.firstname = firstname
          this.lastname = lastname
        }

        setNotes (notes) {
          this.notes = notes
        }

        canPass () {
         return moyenne(this.notes) >= 10
        }

      
      }
      const john = new Student('John', 'Doe')
      const chloe = new Student('Chloé', 'Papin')
      john.setNotes([10, 12, 9])
      chloe.setNotes([15, 13, 20])
      console.log(john.canPass(), chloe.canPass())
```


Ainsi on vas pouvoir voir si la moyenne de ces nottes est supérieur à 10 ou pas. 
On vas donc ré utliser notre fonction pour calculer la moyenne. 

On voit donc qu'on peut créer tout un tas de méthodes qu'on peut metre sur notre "prototype" Student et qui va seras utilisable par tout les objets. 

Après il y as des méthodes qu'on vas définires et qui seront appellées automatiquement. 

## Méthode automatique Getter & Setter

Au lieux d'utiliser une méthode setNotes on veut mettre des notes d'une autres façons : 

```js
 const john = new Student('John', 'Doe')
      const chloe = new Student('Chloé', 'Papin')
      john.notes([10, 12, 9])
      chloe.setNotes([15, 13, 20])
      console.log(john.canPass(), chloe.canPass())

```
Ici on remplace la méthode setNotes par notes. Cela fonctionne quand même, et quand on fait appel à .canPass() on voit que c'est quand même calculer. 

Le soucis est que si on veut ajouter qu'une seul, la script plante (car on attends un tableau). 

On vas donc devoir définir des Getter et Setter. 

### Les Setters (définir une donnée)

Ils seront automatiquement appelés quand on vas définir une valeur. 

On peut créer une méthode notes() qui prendras en paramètre la valeur de la notes qu'on veut mettre et ensuite elle peut faire un code particulier. 

Pour la définir comme un setter on vas devoir utliser le mot clé 'set' suivis d'une espace. 

```js

set notes (v) {
  this.notes = v
}

```
Mais on voit que la situation ne s'améliore pas vraiment, car on a une nouvelle erreur : 

"Maximum call stack size exceeded".

![error Js](/JS%20Basics/assets/ErrorMaxCall.png)

Car quand on fait un this.notes il essai d'aller chercher le setter, mais du coup il s'appel en boucle et donc il plante. 

Donc on peut pas appeller le this .notes. On vas pouoir l'écrire  :

```js

set notes (v) {
  this._notes = v
}

```
Du coup, on vas avoir un problème avec la méthode setNotes qui ne seras plus définis comme une fonction. 
 
 On peut donc remplacer notre 


 ```js
    chloe.setNotes([15, 13, 20])
 ```

 Par : 

  ```js
    chloe.notes([15, 13, 20])
 ```

 Avantage qu'on as maintenant des méthodes, on vas pouvoir faire des vérifications et dans notre cas, vérifier qu'on à bien un tableau. 

 La méthode isArray() est une méthode qui éxiste déjà dans l'objet Array. 

 Avant tout on vas définir les _notes comme un tableau vide 

  ```js
    _notes = []
 ```

 Puis on vas conditionner avec une boucle 'if' pour vérifier si il s'agit bien d'un array 

 ```js
set notes (v) {
  if(Array.isArray(v)){
  this.notes = v
  }
}
 ```
 On vas donc remplir le tableau des notes et dans le cas contraire, on ne feras rien car on part de l'idée que c'est une erreur. 

 ```js
 class Student {
        ecole = 'Jules Ferry'
        _notes = []


        constructor(firstname, lastname) {
          this.firstname = firstname
          this.lastname = lastname
        }

        set notes (v) {
          if(Array.isArray(v)){
            this.notes = v
          }
        }

        canPass () {
         return moyenne(this.notes) >= 10
        }

      
      }
      const john = new Student('John', 'Doe')
      const chloe = new Student('Chloé', 'Papin')
      john.notes([10, 12, 9])
      chloe.notes([15, 13, 20])
      console.log(john.canPass(), chloe.canPass())
```


### Les Getters (accéder à une donnée)

