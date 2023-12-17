# Les fonctions courantes 

Nous allons retracer les méthodes les plus courantes. Il ne s'agit pas de toutes les retenirs. Mais simplement d'avoir une liste comme aide mémoire. 

## Les tableaux

### ".at()"

```js
    const notes = [1, 3, 4, 18]
    console.log(notes.at[0])

    //On vas alors récupérer 1

     const notes = [1, 3, 4, 18]
    console.log(notes.at[-1])

    //On vas alors récupérer 18. s
```

Il s'agit d'une méthode qui permet de récupérer des index. Mais elle permet aussi d'avoir des index négatives. C'est la tout son intéret. 

On vas pouvoir alors récupérer la dernière valeurs. 

### ".concat()"

```js

const array1 = [a, b, c, d]
const array2 = [e, f, g, h]

const array3 = array1.contact.(array2)
console.log(array3);

//  On vas alors avoir un nouveau tableau le "array3"
//  qui vas alors retourner : [a, b, c, d, e, f, g, h ] 

```

Méthode qui permet simplement de contactener des tableaux ensembles pour pouvoir les fusionner.  

### ".filter()"

```js

const notes = [12, 18, 9, 10, 20]
const goodNotes = note.filter((notes) => note >= 10)
console.log(goodNotes)

```

Méthode qui permet de filtrer les résultat que nous renvois un array. 
Quand on vas faire appel à elle cette méthode vas prendre en premier paramètre chaques éléments du tableau et notre fonction vas retourner true ou false. 

Dans notre cas on vas retourner "true" si la notes est supérieur ou égale à 10. Ici filter est donc très utile pour organiser nos éléments de nos arrays par rapport à nos critère. 

### ".find()"

```js

const array1= [5, 12, 10, 130, 44]

const found = array1.find(element => element > 10);
console.log(found)

// On s'attends à récupérer 12. 

```

Méthode qui permet de récupérer le 1er éléments d'un tableau qui vas correspondre à nos conditions. 

### ".findIndex()"

```js

const array1= [5, 12, 130, 44]

const isLargerNulmber = array1.findIndex(element => element > 10);
console.log(isLargerNulmber)

// On s'attends à récupérer 2. 
// IL n'y as que 130 qui es > à 13 et en premier.

```

Méthode qui permet de récupérer l'index du 1er éléments d'un tableau qui vas correspondre à nos conditions. 

### ".findLast()"

```js

const array1= [5, 12, 10, 130, 44]

const found = array1.findLast(element => element > 45);
console.log(found)

// On s'attends à récupérer 130. 

```

Méthode qui permet de récupérer le dernier éléments d'un tableau qui vas correspondre à nos conditions. 

### ".findLastIndex()"

```js

const array1= [5, 12, 130, 44]

const found = array1.findLastIndex((element) => element > 45);
console.log(found)

// IL n'y as que 130 qui es > à 45 et en dernier.
// Donc on vas récupérer 2

```

Méthode qui permet de récupérer l'index du du dernier éléments d'un tableau qui vas correspondre à nos conditions. 

### ".flat()"

```js

const arr1 = [0, 1, 2, [3, 4]]

console.log(arr1.flat())
//On s'attends à recevoir Array [0, 1, 2, 3, 4] 

const arr2 = [0, 1, [2, [3,[4,5]]]]
console.log(arr2.flat())
//On s'attends à recevoir Array [0, 1, 2, Array [3, Array [4, 5]]] 

console.log(arr2.flat(2))
//On s'attends à recevoir Array [0, 1, 2, 3, Arrat [4, 5]]

console.log(arr2.flat(Infinity))
//On s'attends à recevoir Array [0, 1, 2, 3, 4, 5]

```
Méthode qui vas nous permettre de créer un nouveau tableau contenant les éléments des sous-tableaux du tableau qu'on auras mis en argument, qui sont concaténés récursivement pour atteindre un niveau de profondeur qu'on auras donnée.

### ".forEach()

```js

const notes = [12, 17, 18, 8, 9]
notes.forEach((notes, index)=>{
    console.log(notes, index)
})

//Je dois avoir chaques notes du tableau et leurs index dans l'array. 
// 12 0 
// 17 1
// etc...

```

Méthode trés utilisé avant le forOff. Elle permet d'exécuter une fonction précise sur chaques élément du tableau. 

Avantage est qu'elle peut recevoir en paramètre la valeur et l'index. DOnc si on veut faire des opérations à la fois sur l'index et sur les éléments ça nous seras utile. 


### ".from()"
```JS
console.log(Array.form('foo'));
// Je m'attends à avoir Array ["f","o","o"]

console.log(Array.from([1, 2, 3], x => x + x));
// Je m'attends à avoir Array [2, 4, 6]

```
Méthode qui vas nous permettre de créer un tableau à partir de différente chose. 
Si c'st une string alors on vas avoir un tableau avec les différentes lettres une à une. 
Si on lui place un tableau avec certains paramètres, on auras alors un tableau ou notre fonction vas s'appliquer sur tout les éléments du tableau. Mais c'est très rare. On vas préférer Map. 

Cette méthode fonctionne très bien avec les choses itérables. On as pas grand chose de itérable hormis les strings. Donc garder le en tête. 

### ".includes()"
```JS

const array1 = [1, 2, 3]

console.log(array1.includes(2))
//Je m'attends à avoir true.

const pets = ['cat', 'dogs', 'monkey']
console.log(pets.includes('cat'))
//Je m'attends à avoir true.

console.log(pets.includes('cow'))
//Je m'attends à avoir false.

//On peut créer une condition if 
if(['b', 'c', 'd'].includes(a))

```

Méthode qui permet de déterminer si un tableau continet une valeur et renvoie "true" si c'est le cas, "false" sinon


### ".indexOf()"

```js

const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

console.log(beasts.indexOf('bison'));
// Position 1 retourné

// Start from index 2
console.log(beasts.indexOf('bison', 2));
// Je m'attends à avoir :: 4

console.log(beasts.indexOf('giraffe'));
// Position -1 retourné car non présent dans le tableau


```
Cette méthode est un peu comme le ".find()". Sauf qu'on peut lui passer directement une valeur. La valeur seras alors trouver dans le tableau et ça vas nous renvoyer l'index de la valeur. Utile pour savoir si la valeur éxiste dans un tableau. Si jamais la valeur retourner est -1 c'est que l'élément ne fait pas parti du tableau. 
Très utilisés avant que les includes n'arrivent. 


### ".join()"

```JS

const elements = ['Fire', 'Water','Air'];

console.log(elements.join())
// Je m'attends à avoir "Fire,Water,Air"

console.log(element.join(''));
// Je m'attends à avoir "FireWaterAir"

console.log(element.join('-'));
// Je m'attends à avoir "Fire-Water-Air"
```
Méthode qui permet de créer et de retourne une nouvelle string en concaténant tous les élément d'un tableau  (ou objet qui ressemble à un tableau).
La concaténation utilise la virgule ou une autre chaine, fournis en argument, comme séparateur. 


### ".map()"

```JS

const array1 = [1, 4, 9, 16];

// Passer une function pour map
const map1 = array1.map((x) => x * 2);

console.log(map1);
// Je m'attends à avoir Array [2, 8, 18, 32]


```


Peut être l'une des méthodes les plus importantes qu'on vas rencontrer. 
Cette méthode vas prendre en 1er paramètre une fonction qui vas pemettre d'altérer les éléments. 
On peut imager cette fonction comme une fonction de transformation d'un tableau. 

Ici elle prendre un tableau de 4 éléments et vas appliquer une transorfmation sur tout les éléments à chaques fois. 
On as donc expliquer que x serais = à un tableau ou toutes les valeurs de x seront multipler par 2. 

C'est vraiment très utile pour transformer des tableaux. 

```JS

const persons = [
    {firstname: 'Jhon', lastname: 'Doe'},
    {firstname: 'Jean', lastname: 'Doe'},
    {firstname: 'Jacques', lastname: 'Doe'},
    {firstname: 'Manon', lastname: 'Doe'},
]
console.log(
    persons
    .map((p) => p.firstname + ' ' + p.lastname)
    .join('\n')
)

```
Map renveras toujours un tableau de la même taille que l'original. 


### ".pop()"


```JS 

const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

console.log(plants.pop());
// Je m'attends à avoir tomato

console.log(plants);
// Je m'attends à avoir Array ["broccoli", "cauliflower", "cabbage", "kale"]

plants.pop();

console.log(plants);
// Je m'attends à avoir Array ["broccoli", "cauliflower", "cabbage"]

```

Pop() est une méthode qui permet de retirer le dernier élément d'un tableau et de retourner cette élément. 
Attention cette méthode vas changer la taille d'un tableau. 

### ".push()"

```JS
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count);
// Je m'attends à avoir :: 4
console.log(animals);
// Je m'attends à avoir :: Array ["pigs", "goats", "sheep", "cows"]

animals.push('chickens', 'cats', 'dogs');
console.log(animals);
// Je m'attends à avoir :: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]
```

Cette méthode vas vous permettre d'ajouter un ou plusieurs éléments à la fin d'un tableau et de retourner la nouvelle taille du tableau. 

### ".reduce()"

```js

const notes = [12, 18, 19]
console.log(
    notes.reduce((acc, notes) => acc + notes, 0)
)
// Je m'attends donc à recevoir la somme de mon tableau 49

```

Peut être une des méthodes les plus complexes quand on débute. Mais c'est une des méthodes les plus puissantes. 

Permet de lire les éléments de gauche à droite. 

Comme on l'as vue dans d'autre chapitre quand on veut faire une sommes de notes par exemple, on vas devoir faire une boucle. Donc y as rien de mal à ça, mais "reduce" vas beaucoup nous aider la dessus. 

Cette méthode prends en premier paramètre une callback et ce callback auras deux paramètres. 

Le premier paramètre auras un "accumulateur" (souvent nommé acc) et en seconde paramètre la valeur courrante (dans notre cas la notes sur laquelle on se trouve). 
Dans cette fonction on vas retourner une valeur.

En seconde paramètre de notre méthode, on vas lui donner une valeur de départ. Cette valeur seras alors placé dans l'accumulateur.

Méthode très utile quand on veut additionner toutes les valeurs d'un tableau pour en ressortir qu'une seule valeur. 

### ".reduceRight()"

Même fonction que pour la méthode ".reduce()", mais on vas parcourire les éléments de gauche à droite. 

### ".reverse()"

```JS

const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// Je m'attends à avoir : "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// Je m'attends à avoir : "reversed:" Array ["three", "two", "one"]

// Attention car cette méthode vas changer la nature du tableau.
console.log('array1:', array1);
// Je m'attends à avoir : "array1:" Array ["three", "two", "one"]


```

Permet d'inverser l'ordre des éléments dans un tableau. 



### ".shift()"

```JS

const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(array1);
// Je m'attends à avoir Array [2, 3]

console.log(firstElement);
// Je m'attends à avoir: 1

```

Cette méthode permet de retirer le premier élément d'un tableau et de retourner cet élément. Mais attention cette méthode modifie la longueur du tableau. 


### ".slice()"

```js

const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// Je m'attends à avoir : Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// Je m'attends à avoir : Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// Je m'attends à avoir : Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// Je m'attends à avoir : Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// Je m'attends à avoir : Array ["camel", "duck"]

console.log(animals.slice());
// Je m'attends à avoir : Array ["ant", "bison", "camel", "duck", "elephant"]


```

Cette méthode permet de retourner une copie du tableau moins les éléments qu'on auras retirés du tableau. On peut ajouter un paramètre qui vas marquer le début et la fin de notre slice. 
Si jamais la valeur qu'on lui donne en fin est négative, alors il commenceras le slice par la fin. 
L'avantage est de pouvoir créer un nouveau tableau après le slice().

```JS

const notes = [12, 18, 19]

const reverseSliceNote = notes.slice().reverse()
// Je m'attends à avoir [19, 18, 12]

```

### ".sort()"

```js

const months= ['march', 'Jan','Feb', 'Dec']
months.sort();
console.log(months)
//Je m'attends à avoir ["Dec", "Feb", "Jan", "March"]

const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// Je m'attends à avoir : Array [1, 100000, 21, 30, 4]

```

Sort vas nous permettre d'organiser les éléments dans un tableau. Par défaut le tri s'effectue sur les éléments du tableau convertis en string et triées selons les valeurs des unites de code UTF-16. 

### ".unshift()"

```JS

const array1 = [ 1, 2, 3]
console.log(array1.unshift(4, 5))
// Je m'attends à avoir : 5

console.log(array1)
// Je m'attends à avoir : [ 4, 5, 1, 2, 3]

```

Cette méthode ajoute un ou plusieurs éléments au début du tableau et retourne la nouvelle longueur du tableau. 

