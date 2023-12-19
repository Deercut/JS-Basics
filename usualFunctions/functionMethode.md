# Les fonctions

Nous allons voir qu'il y as très peut de méthode utiles sur les functions. 
Elles vont surtout nous permettres de jouer avec "this".

## ".prototype.bind()"

```JS

function hello() {
    console.log(this)
}

const hello2 = hello.bind(3)

// Je m'attends à recevoir : hello2() NUmber{3}


```

Cette méthode permet de créer une fonction à partir d'une fonction en changeant le context de "this". L'intérêt est de pouvoir ancrer la valeur et de ne plus pouvoir la bouger. 
Mais si on essais de rebinder notre fonction derrière le premier bind, le second bin seras quand même ignoré. 

## ".prototype.apply()"

```JS

const numbers = [5, 6, 2, 4, 7]
const max = Math.max.apply(null, numbers);

console.log(max);
// Je m'attends à avoir : 7 

const min = Math.min.apply(null, numbers);
// Je m'attends à avoir : 2

```

Cette méthode apple une fonction en lui passant une valuer this et des arguments sous forme d'un tableau (ou d'un objet qui ressemble à un tabLeau). 

## ".call()"

```JS 

function Product(name, price){
    this.name = name;
    this.price = price;
}

function Food(name, price){
    Product.call(this, name, price):
    this.category = 'food';}

console.log(new Food('cheese', 5).name);
// Je m'attends à avoir : "cheese"

```

Cette méthode fait un appel à une fonctionj avec une valeur de this donnée et des argument fournis les un à côtés des autres. 