# Le sucre synthaxique

De quoi ça parle ? Il s'agit d'une façon plus simple et plus rapide d'écrire certaines choses en JS. 

## Les nombres

Prennons l'exemple des nombres 

```JS

let i = 0 
console.log(i++)
// On s'attends à avoir zero. Car c'est la valeur AVANT incrémentation.
console.log(++i)
// La on auras la valeur de i après incrémentation

```

Autre exemple avec des additions ou soustractions

```JS

let i = 3
//On pourais faire
i = 3 + 3 

Dans ce cas autant faire directement 

i += 3
console.log(i)
// On auras 6

```

## Les fonctions fléchèes.

On l'as vue on peut avoir une fonction qui renvois directement le résulta en ne métant qu'une instruction.

```JS

const double = (n) => n * 2
console.log(double(3))

// Je m'attends à avoir 6

```

Si la méthode fléché n'as qu'un seul paramètre (comme c'est le cas avec notre exemple), on vas alors pouvoir directement retirer les parenthèses.

## Les conditions

Prennons l'exemple d'une conditions qui vérifie si "a" as bien la bonne valeur.

### "||" "OU"

```JS

const a = 3
const b = a || 5
console.log(b)

// Je m'attends à recevoir 3. 
// Si j'avais mis  a = 0 
// 0 étant une valeur fausse alors j'aurais eu 5

```
Si on fait, quelques chose "ou" ( || ) quelque chose, on vas tester la valeur de a de référence et voir si elle renvoit true OU false. 

On peut le pratiquer avec des fonctions également 

```JS
const a = 3
const b = fn1() || fn2()
console.log(b)

// Si fn1() est vérifié alors fn2() ne seras jamais exécuté. 

```
### "??" 

Le ?? est comme || mais la valeur de a devra être null ou undefined pour que la valeur en face soit utilisée

```JS

const a = 0
const b = a || 5
console.log(b)

// Je m'attends à recevoir 0
// Mais si const a était let a 
//ALors la valeur retournée serais 5
```

### "&&" "ET"

```JS
const a = 3
const b = fn1() && fn2()
console.log(b)

// Si fn1() renvoie true alors fn2() seras éxécuté. 
// Si fn1() renvoie false alors fn2() ne seras pas éxécuté.
// b retourneras alors que la fonction fn1()

```

### Le "?"

Bien pratique pour avoir accès à une propriété un peu cachée dans un objet, on pas pouvoir tester si la propritété est présente ou pas. 

```JS

const person = {firsname : 'John'}
console.log(person.job?.name)
// Ici avec le ? on vas appeller la propriété name celui et celui ci celle ci est définis. Si "job" ou "name" est undifined alors on retourneras "undifined".

const person = {firsname : 'John'}
console.log(person?.age?.toString())

// Ici on vas pouvoir ne lancer toString que si age et personne sont définit. 


```

## Le destructuring

Avant le destructuring on aurais du faire quelques choses comme ceci : 

```JS

const notes = [12, 17, 18]
const premierNotes = notes[0]
const secondeNotes = notes[2]

// Pas ultra efficace

```

Avec le destructuring on pas pouvoir dans la partie de déclaration du nom de notre variable, on vas pouvoir utiliser un array et y déposer le nom de nos constantes.

```JS

const [premierNotes, secondeNotes] = [12, 17, 18]

console.log(premierNotes, secondeNotes)
//Je m'attends à avoir 12 et 17

```

Dans ce cas le 12 seras attribué à la variable premierNotes et le 17 à la variable secondNotes.

Mais je peut aussi récupérer toutes les autres notes d'un coup.

```JS

const [premierNotes, ...autresNotes] = [12, 17, 18, 19]

console.log(premierNotes, autresNotes)
//Je m'attends à avoir 12 et [17, 18, 19]

```

### Destructuration object

Ceci fonctionneras aussi avec les objets. 
Il prendras la propriété firstname et la placeras dans la varialbe prenom.

```JS

const {firstname: prenom} = {
    firstname: 'John',
    lastname: 'Doe',
    age: 18
} 
console.log(prenom)
// Je m'attends à avoir John


const {irstname, lastname} ={
    firstname: 'Michel',
    lasname: 'Bacry',
    age: 70
}

console.log(firstname,lastname)


//Comme pour les nombres on vas pouvoir utiliser un rest opérateur (...)

const {irstname, ...rest} ={
    firstname: 'Michel',
    lasname: 'Bacry',
    age: 70
}
console.log(firstname,rest)

```
 
 Ceci seras très utile pour les fonctions. 
Imaginon qu'on es une fonction qui attende un objet avec les données utilisateurs et surtout l'age et le pays. 

 ```JS

function canDrive ({age, pays}){
return true
}

// L'age seras dans la propriété age et pays dans pays. 

 ```

 Mais que ce passe t'il si demain on as besoin de la région en plus ? On aurais alors à simplement rajouté la propriété région dans notre fonction pour que cela fonctionne. 

  ```JS

function canDrive ({age, pays, region}){
return true
}
canDrive({age: 18, pays: 'France', region: 'Lille'})
// L'age seras dans la propriété age et pays dans pays. 

 ```

 On se rends compte qu'on vas gagner en flexibilité. 
 Chose interessante on as aussi pouvoir attribuer une valeur par défaut. 

 Par exemple si on as pas région, on peut très dire que par defaut ça seras Pairs. 

 On évite ainsi le "undefined"

   ```JS

function canDrive ({age, pays, region="Paris"}){
    // En mettant Paris par défaut on évite alors de devoir faire un if
    if(region === undefinend){
        region = "Paris"
    }
return true
}
canDrive({age: 18, pays: 'France', region: 'Lille'})

 ```

 ### Manipulation tableau et objet

 Nous avons un tableau avec deux numbers. Si on veut ajouter des numbers à notre tableau on vas devoir utiliser une méthode comme push. 
 Mais si on fait ça on vas alors modifier le tableau qui es retourné. 

 On peut le faire avec une autre synthaxe. Cette synthaxe consiste en un nouveau tableau avec un "..." dedans 

 ```Js

const notes = [1, 3]

const newNotes = [...notes, 10, 2]
console.log(newNotes)
//Je m'attends à recevoir les notes du premier tableau suivie des deux nouvells notes que j'ai ajoutées. 

//ON peut également inverser le sens de nos éléments et placer nos notes à la fin. 

const newNotes = [ 10, 2, ...notes]

 ```

 Contrairement à push, le tableau d'origine resteras inchangé. 

 Plutot utile quand on vas vouloir rajouter des tableaux et manipuler nos éléments. 

 Par exemple pour changer l'ordre d'un tableau on vas souvant pouvoir faire :

 ```JS

const notes = [1, 2, 3]

const newRevers = [...notes].reverse()
//Ainsi on auras un nouveau tableau qui seras reverse, mais on vas pas toucher au 1er tableau. 

 ```

 On peut le faire également avec les objets. 

 ```JS

const person = {firstname = "Jean", lasname="Bibou"}

const agePerson = {...person, age:18}
//On auras donc un nouvel objet mais qui reprendras les propriétés de l'ancien en lui ajoutant l'âge. 

 ```

 ### Le sucre des conditions "Les ternaires"

 Partons de l'idée de créer une constante age= 18. On voudrais afficher un message pour savoir si la personne à 18ans ou pas. 

 On seras donc obligé de créer une variable message ne pas lui donenr de valeur de lui mettre une condition ...


 ```JS 

const age = 18 
let message

if(age >= 18 ){
    mesasge = "Majeur"
} else {
    message = "Mineur"
}
console.log(message)
 ```
 
 On vas pouvoir faire beaucoup plus simple en créant des ternaires. C'est une synthaxe qu'on vas retrouver très souvent et qui est juste parfaite. Car on vas la retrouver dans beaucoup de langage. 

  ```JS 

const age = 18 
let message = age >= 18 ? 'Majeur' : 'Mineur'
console.log(message)
 ```
 On as donc quelques choses de bien plus joli dans le cas d'un if condition else. 