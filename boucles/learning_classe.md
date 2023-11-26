# Entrainement avec les classes

## Création de classes avec prototype


Partons du principe qu'on vas créer des classes avec des formes géométriques. 

Mais on vas utiliser des "getter" spécifique qui vous permettres d'avoir le périmètre du rectangle et une méthode isValide pour savoir si la dimension est positive ou négative. 


```js

const r = new Rectangle(10,20);
console.log(r.perimeter)
console.log(r.isValide)
const r2 = new Rectangle(-10,20);
console.log(r.isValide)
const c = new Square(10);
console.log(c.perimeter)
console.log(c.isBiggerTahn(r))

```

On vas devoir se retrouver à créer getter et classes pour que tout notre code fonctionne correctement. 


### Le système de rectangle 

D'abords créer la classe rectangle qui auras donc des paramètres (largeur et hauteur). 

Pour rappel on construit nos paramètres avec "construtor". 
N'oubliez pas d'initialiser nos propriétés dans notre objets pour les utilisers plus tard. 

#### Classe rectangle

```js
class rectangle {
    constructor (width, height){
        this.width = width
        this.height = height
    }
}
```
Pour le moment nous aurons toujours perimeter à "undefined" car nous n'avoir pas de propriétés définis. 

#### Ajout getter perimètre

On vas donc créer un getter perimeter qui vas nous retourner le périmetre de notre rectangle. 

```js
class rectangle {
    constructor (width, height){
        this.width = width
        this.height = height
    }
}
get perimeter () {
    return (this.widht + this.height) * 2
}
```

#### Cas de isValde

Traitons le cas de isValide. Comme nous allons y accéder comme simplement proprité on as besoin d'un nouveau getter. 

```js
class rectangle {
    constructor (width, height){
        this.width = width
        this.height = height
    }
}
get perimeter () {
    return (this.widht + this.height) * 2
}

get isValid() {
    return this.width > 0 && this.height > 0
}
```
Le premier test sur la première forme est valide (notre r). Mais on à un retourne false car notre deuxième forme (r2) elle n'est pas valide. 

#### Classe carré.

Comme un carré est un simple rectangle particulier on vas pouvoir le créer en se basant sur l'héritage. 

```js
class Square extends Rectangle {
    constructor(widht)
}
```
Maintenant on vas avoir besoin d'initialiser nos propriétés. 

On vas pouvoir le faire en faisant appel au constructeur parent via le mot clé "super". 
On pourras alors lui donner la largeur mais également la hauteur en donnant la même valeur que la largeur. 

```js
class Square extends Rectangle {
    constructor(widht) {
        super(width, hight)
    }
}
```

Maintenant que cela es fait il ne nous reste plus qu'à gérer le méthode isBiggerThan. 

On pourras la metre uniquement pour le carré mais ça peut aussi servir pour le rectangle. 

#### Création de la méthode isBiggerThan.

```js
isBiggenThan (shape) {
    return this.perimeter > shape.perimeter
}
```

On as donc notre méthode qui prends une shape en paramètre. 
Notre fonction vas retourner un boolean pour savoir si le perimetre de C (donc notre carré ) et plus grand que celui de R (notre rectangle)

### Conclusion premier exercice.

Les classes c'est pas plus compliqué que cela. Le plus difficile est de savoir comment on vas découper les choses pour s'organiser. 


## Exercice de gestion de livre

```js

const b = new Book('Lord of the ring')
console.log(b.page)
b.nextPage()
console.log(b.page)
b.close()
console.log(b.page)

const l = new Library();
l.addBook(b)
l.addBook([
    new Book ('The Witcher', 300)
    new Book ('Oui oui ', 30)
    new Book ('Dune', 3000)
])
l.findBooksByLetter('T') //utilisation de filter
```
 
Dans notre cas présent on vas vouloir gérer une librairie. Pour cela on vas utiliser des objets encore une fois. 

On vas avoir besoin de deux classes, une classe pour gérer le livre, qui seras constitué de deux informations, son titre et le nombre de page.

On vas ensuite avec une méthode pour tourner la page et de faire next page pour aller à l apage suivante. 
Du coup quand on vas loger la page, on devrat être à la page 2. 

On auras aussi un bouton close qui vas permettre de fermer notre livre. 
Tout comme la possibilité d'ajouter un books. 

On aura également une méthode pour trouver le titre d'un livre avec la première lettre de ce dernier. 


### Ajout de la class Book. 

Créons dabords la classe Book pour gérer notre livre uniquement. 

```js
class Book {
    constructor (title, pages){
        this.title = title
        this.pages = pages. 
    }
}
```

Ensuite on vas devoir créer une nouvelle propriété "privé à notre Book pour récupérer la page. 

```js
class Book {

    #page = 1

    constructor (title, pages){
        this.title = title
        this.pages = pages. 
    }
    get page() {
        returne this.#page
    }
}
```
 Ici on peu faire un getter et lui retourner this.#page car on reste dans la classe Book et qu'on peut accéder au propriété privé.

 On vas ajouter une méthode nextPage() pour tourner la page. Mais attention si on es à la fin on ne peut pas retourner une page. 
 On vas donc devoir faire une condition pour empécher cela. 


 ```js
class Book {

    #page = 1

    constructor (title, pages){
        this.title = title
        this.pages = pages. 
    }
    get page() {
        returne this.#page
    }

    function nectPage () {
        if (this.#page < this.pages){
            this.#page++
        }
    }
}
```

Maintenant que cela es fait on vas avoir besoin de créer notre méthode close. Qui vas se chargedr de re initialiser nos page. 

 ```js
class Book {

    #page = 1

    constructor (title, pages){
        this.title = title
        this.pages = pages. 
    }
    get page() {
        returne this.#page
    }

    function nectPage () {
        if (this.#page < this.pages){
            this.#page++
        }
    }

    function close (){
        this.#page = 1
    }
}
```
Maintenant qu'on as gérer notre livre, on vas devoir gérer notre bibliothèe encitère. 

Ici on vas avoir notre class Library qui vas pouvoir ajouter un livre (en prenant en paramètre un book)

Une méthode add books pour ajouter plusieurs livre 

Et une dernière méthode pour trouver notre book par la lettre. 

Pour gérer nos Books on vas pouvoir créer un tableau privé de Book. 
```js 
class Library {

    #books = []

    addBook(book) {
        this.#books.push(book)
    }

    addBooks(books) {
        for(let book of books){
            this.addBook(book)
        }
    }

    findBooksByLetter(letter){
        const found =[]
        for(let book of this.#books){
            if(book.title[0].toLowerCase === letter.toLowerCase){
                found.push(book)
            }
        }
        return found
    }
}
```
Ici on as une première façon assez simple de gérer notre library. Mais pour la recherche on peut améliorer cela avec une méthode JS "filter".


```js
findBookByLetter(letter){
   return this.#books.filter((book) => book.title[0]..toLowerCase === letter.toLowerCase)
}
```

Le plus compliqué avec les classes c'est de trouver une bonne organisation. Il faut réussir à savoir comment on vas décomposer notre code. 

```js
    addBooks(books) {
        for(let book of books){
            this.addBook(book)
        }
    }
```

Pour cette section, nous avons déjà une méthode foreach qui pourrait nous aider à simplifier un petit notre code. Plus que for of. 

foreach est une méthode qui prends en paramètre une fonction, et cette fontion sera appellé pour tout les éléments. 

```js
    addBooks(books) {
        books.foreach(this.addBook, this)
    }
```
Pourquoi ajouter this en paramètre de notre méthode foreach ? 
Quand on passe des méthodes directement à d'autres fonction il faut faire attention à ce que ces fonctions ne modifies pas this. Sinon on vas avoir des soucis. 

Mais on peut aussi résoudre le problème autrement. En utilisant une fonction fléché. 

```js
    addBooks(books) {
        books.foreach((book) => this.addBook(book))
    }
```
Car dans une fonction fléché this ne seras jamais modifié. Du coup this fait bien référence à ce qu'on retrouve dans notre fonction addBook.

