# Les objets

## ".assign()"

```JS

const target = {a:1, b:2}
const source = {b:4, c:5}

const returnedTarget = Object.assign(target, source)

console.log(target)
// Je m'attends à avoir : Objet {a: 1, b:4, c: 5 }
console.log(returnedTarget === target)
// Je m'attedns à avoir : true


```
Cette méthode permet d'assigner des des méthodes d'un objet à un autre objet. 
Cette méthode est un peu ancienne et seras plutôt remplacé par le spread.

Mais l'avantage est que .assigne() vas nous retourner un nouvel objet, mais qui reprends les mêmes propriétés que l'autre objet. 

## ".creat()"

```JS

const person = {
    isHuman : false,
    printIntroduction : function() {
        console.log(`My name is ${his.name}. AM I human ? ${this.isHuman}`);
    }
};
const me = Object.create(person);

me.name = 'Mattew' //name est une propriété set de "me" mais pas une "perso".
me.printIntroduction();
// Je m'attends à avoir : "My anme is Mattew. Am I human? true

```

Cette méthode permet de créer un nouvel objet en utilisant le prototype d'un autre objet et retourneras un nouvel objet.

C'était assez utile à l'époque ou on n'utilisait pas tellement les classes.   

## ".defineProperties()"

```JS
class A {

    constructor() {

    }
    set field (v) {
        console.log('hello')
    }
    const a = new A();
    Oject.definePorperty( a, 'field', {
        value: 3
    })
}
//Je m'attends à avoir : Objet A{field: 3}
```

Cette méthode permet de définir une propriété sur un objet. On vas ainsi pouvoir outrepasser le setter d'un objet. 

## ".entrties()"

```js

const person = {firstname: "Bibouch", lastname: "Olive"}
console.log(Object.entries(person))

// Je m'attends à avoir un Arra : [Array(2), Array(2)]
// 0: (2)['firstname', 'Bibouch']
// 1: (2)['lastname', 'Olive']
// length : 2
// [[Prototype]] : Array(0)

```

Cette méthode permet de renvoyer un tableau avec des clés et valeurs. 
Ce seras très utilie lors de la destructuration. Exemple en faisant une boucle for of sur les objets. 
Permet alors de faire une boucle et de récupérer la clé et la valeur dans les propriétés de l'objet. 

## ".freeze()"

```JS

const objt = {
    prop: 42,
};

Object.freeze(obj);

objet.prop = 33
// Renvois uen erreur de strict mode

console.log(obj.prop)
// Je m'attends à avoir: 42

```

Dans le cadre d'optimisation de code, cette méthode permet de géler l'utilisation d'un objet. On vas donc empécher la possibilité de lui ajouter de nouvelle propriétés, de supprimer, ou d'éditer des propriétés existantes. 

## ".is()"

```JS

Object.is("toto", "toto"); // true
Object.is(window, window); // true

Object.is("toto", "truc"); // false
Object.is([], []); // false

var toto = { a: 1 };
var truc = { a: 1 };
Object.is(toto, toto); // true
Object.is(toto, truc); // false

Object.is(null, null); // true

// Cas aux limites (cas spéciaux)
Object.is(0, -0); // false
Object.is(-0, -0); // true
Object.is(NaN, 0 / 0); // true

```

Cette méthode permet de détermine si deux valeurs sont les mêmes. Une sorte ===. Mais ça peut permettre de comparé deux zéro négatif ainsi que deux NaN ensemble. 

## ".keys()"


```JS

const person = {firstname: "Bibouch", lastname: "Olive"}
console.log(Object.keys(person))

//Je m'attends à avoir : Array 2 ['firstname', 'lastname']

```

Cette méthode permet de retourner un tableau de toutes les clés. Très intéressant pour pouvoir faire des boucles ensuite. 

Si jamais on ne veux que les valeurs on peut utiliser .values().

```JS

const person = {firstname: "Bibouch", lastname: "Olive"}
console.log(Object.values(person))

//Je m'attends à avoir : Array 2 ['Bibouch', 'Olive']

```