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
7min18


