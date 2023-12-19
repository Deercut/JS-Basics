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

```