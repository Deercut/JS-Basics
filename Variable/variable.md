<!--
************************* 01-Les Varialbes *************************

Pour toutes documentations sur JS 

https://developer.mozilla.org/fr/docs/Web/JavaScript




Pour déclarer une variable il est nécessaire de commencer
avec "const" (pour constante)

    const a = 3;
    let a = 4;

En js on peut finir avec un ";", mais c'est pas obligé non plus.     

Si vous définissez votre variable avec "const", vous ne pourrez plus changer sa valeur dans le future. 

Mais avec "let", vous pourrez changer la valeur de la variable. 
Vous pouvez également utiliser "var", mais ce n'est plus vraiment utilisé. 

Vous pouvez également ne rien noté : 

    a = 3

Ce qui seras = à var a = 3. Mais il es important de toujours bien renseignez votre variable. 


On as vue qu'on peut mètre des nombres entier, à virgule, un string.

Si jamais vous voulez utiliser des ' vous allez devoir mètre des échapement. C'est = à un \
EX : 'Ajourd\'hui';

Mais on peut passer outre avec des " ". 
    a = "Hello world";  
    a = 'Ajourd\'hui';
    a = "Aujourd'hui"
        

Concaténer des string : 


On vas pouvoir additioner des strings. 

b + c = Salut les gens

b + ' ' + c = Salut les gens

`${c} ${b}` = Salut les gens


Les booléens : 


On vas retrouver un résultat à "true" ou "false" ou "null" (null pour une absence de valeur).

    const isMajeur = false
    const isMajeur = true
    const isMajeur = null

Si on veut save une chaine de caractère mais qu'elle peut être null alors on auras une chaine vide. 

    const isMajeur = undefined

Assez rare, il permet de dire qu'une varialbe n'est pas définis. Elle est automatiquement attribué à une variable qui n'es pas définis. 


Les tableaux : 


Permettre de save une liste de valeur, liste de notes d'un élève etc etc. 

const notes = [13, 4, 2, 9 , 12]

Mais un tableau peut également avoir une chaine de caractère et même un autre tableau à l'intérieur. 

const notes = [13, 4, 2, 9 , 12, 'hello', [10, 20, 8, 16]]

Pour les tableaux, les éléments sont rangés dans un index. L'index commence comme en Java à 0. 

0, 1, 2, 3, 4 ....

Pour récupérer l'index d'un élément on noteras 

notes[] et dans le [] le numéro qu'on souhaite récupérer. 


notes[5] = 'hello'

Pour accéder à notre deuxième tableaux : 

notes[5][0] = notre deuxième tableau à la position 0. 


Les objets : 

Element un peu plus complexe qu'un tableau qui vas nous permettre de sauvegarder plus de chose, exemple des clés. 


const person = {firstname: 'Jhone' lastname: 'Doe'} 

firstename et lastename sont des prorpiétés de notre objet person. 

 const person = {
        firstname: 'Jhone',
        lastname: 'Doe',
        age: 24,
        notes: [12, 14, 15],
        job: {
            name:"informaticien",
            hours: 35
        }
    } 

On as donc notre objet person qui contient des propriétés, un tableau et un autre objet 'job'. 

Pour accéder à notre objet et à ses propriétés on feras 

person.job.name
person.age
person.notes[1]


notes
(7) [13, 4, 2, 9, 12, 'hello', Array(4)]
notes[1] = 29
29
notes
(7) [13, 29, 2, 9, 12, 'hello', Array(4)]

On peut donc modifier dynamiquement notre tableau. 


Si on veut dynamiquement créer une propriétée on doit la placer entre []. 

  const person = {
        firstname: 'Jhone',
        lastname: 'Doe',
        age: 24,
        notes: [12, 14, 15],
        job: {
            name:"informaticien",
            hours: 35
        },
        [b]: 23
    } 

On peut avoir le type d'une varialbe avec 'typeof'.

typeof 3
typeof notes
typeof b
typeof person


.lenght vas pouvoir nous donner la taille d'un tableau. 


notes.lenght = le nombre d'élémnt présent dans notre tableau notes. 

Tout les types de varialbe sont des objets en js. 


Opérations possibles : 


On peut concatener des strings en les additionnants. 
Idem avec des nombres. 

Mais attentions avec les nombres flottants. Comme tout langage, le js à du mal avec les nombres à virgule. 

On peut également additioner nombre et string. Dans ce cas JS vas alors concidérer que le nombre est un string et automatiquement plutôt que faire une addition il vas concatener les deux valeur. 


4 + "3" = 43. 
3.4 + '2' = 3.42


Avec multiplication '*', si on fait la multiplication d'un nbr et string, js vas alors se dire que le string est un entier. 


2 * '2' = 4
2 * 'A' = Nan (not a number)


On peut pas déclarer deux fois une variable du même nom. Logique mais on ne sait jamais. 

-->

