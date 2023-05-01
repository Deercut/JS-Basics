# Les classes et programmation orienté objet (POO)

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

## Syntaxe des classes


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

### Construire notre élève avec le constructor 

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

### Et si on ajoutait des notes ?

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
