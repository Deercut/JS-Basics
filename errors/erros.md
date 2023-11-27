# Les exceptions en JS

## Pourquoi faire ? 

Les exceptions permettent de déclancher des erreurs quand nous avons des données qui ne sont pas attendues dans notre système. 

On peut faire écho à notre exercice sur les formes géométriques. On aurait bien voulu renvoyer une erreur si jamais la forme ne correspondait pas à ce qui était attendue. C'est à ce moment la que les exceptions arrivent. 

Une erreur est un objet comme les autres, il as des propriétés, prototype ect...

Reprennons l'exemple de nos rectangle et carré. 

```JS
class Rectangle {
    constructor (width, height){
        this.width = width 
        this.height = height
    }
    get perimeter() {
        return (this.width + this.height)
    }
    get isValid() {
        return this.width > 0 && this.height 
    }
    isBiggerThan(shape){
        return this.perimeter > shape.perimeter
    }
}
```
Dans le cas de notre rectangle, on voudrais retourner une erreur si jamais la width ou la height et = 0 

Pour cela on vas jouter une condition qui vas "throw" un message d'erreur.

```JS
class Rectangle {
    constructor (width, height){
        if(width <= 0 || height <=0 ){
            throw new Error('Impossible que la valeur soit négative')
        }
        this.width = width 
        this.height = height
    }
    get perimeter() {
        return (this.width + this.height)
    }
    get isValid() {
        return this.width > 0 && this.height 
    }
    isBiggerThan(shape){
        return this.perimeter > shape.perimeter
    }
}
```

Parfois on vas avoir besoin de capturer une erreur pour pouvoir retourner quelques choses. On vas alors avoir besoin d'un "try" et "catch".

```JS
class Rectangle {
    constructor (width, height){
        if(width <= 0 || height <=0 ){
            throw new Error('Impossible que la valeur soit négative')
        }
        this.width = width 
        this.height = height
    }
    get perimeter() {
        return (this.width + this.height)
    }
    get isValid() {
        return this.width > 0 && this.height 
    }
    isBiggerThan(shape){
        return this.perimeter > shape.perimeter
    }
}

class Square extends Rectangle {
    constructor(width){
        super(width, width)
    }
}

try {

} catch (e){

}

```
Le paramètre (e) est celui qui vas nous retourner l'erreur. Dès qu'une fonction peut nous retourner une erreur on la metras dans la zone du "try".

SI n'importe laquelle des instructions placée dans le try retourne une erreur alors on pourras la mettre dans la zone catch. 

```js
try {
    const r = new Rectangle(-10, 20)
} catch (e){
    console.log(e.message)
}
```
Si on ne veut que le message d'erreur alors on mettras directement e.message

Prennon un autre exemple avec notre Rectangle.

```JS
const width = parseInt(prompt('Largeur'), 10)
const height = parseInt(prompt('largeur'), 10)
const r = new Rectangle(width, height)
console.log(r.perimeter)
```
Maintenant placer cela dans un try catch pour voir les erreurs qu'on vas pouvoir retourner.

```JS
try {
    const width = parseInt(prompt('Largeur'), 10)
    const height = parseInt(prompt('largeur'), 10)
    const r = new Rectangle(width, height)
    console.log(r.perimeter)
} catch {
    console.log(e.message)
}

```