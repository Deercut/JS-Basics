# Les boucles

Les boucles permettent de recommencer des codes en fonctions des certaines condtions. 

## Tant que / while

On execute notre code tant que tel condition ne seras pas vérifié. 

```js
let i = 10 
      while(i<10){
        
      }
```
Ne lancé pas se code comme ça, sinon on arrive dans le cas d'une boucle infinis. On bloqueras notre navigateur. 

```js
      let i = 10 
      while(i < 10) {
        console.log('Bonjour')
        i = i + 1
      }
```

Ici nous allons afficher 'Bonjour' 10x. 
Pour cela on vas faire une incrémentation avec 
i = i + 1. On donc demander d'incrémenter de 1 
et comme on as une boucle while, on vas le faire jusqu'à arrivé à 10. 

On peut aussi le noter :
```js
      let i = 10 
      while(i < 10) {
        console.log('Bonjour' + i)
        i = i + 1
      }
```

C'est la boucle la plus simple, mais également la boucle la plus dangereuse. 

## Pour / for

Il s'agit d'une boucle un peu plus prévisible et vas donc nous permettre de mieux gérer son résultat possible. 

```js
    for (let j = 0 ; j < 10; j = j + 1){
        console.log("Hello");
      }
```

Ici l'écriture est un peu plus conquaténée. 
On as donc la déclaration de notre varialbe 
```js
    let j = 0
```
dans notre boucle. 

Puis nous avons sa condition de sortie après


```js
    let j = 0; j < 10
```

Puis son opération de mise à jours, ici une incrémentation de 1. 

```js
    let j = 0; j < 10; j = j + 1
```

Attention à notre condition de mise à jour, car on peut rapidement avoir une boucle infinis. 

Il y as une façon un peu plus rapide d'écrire notre condition de sortie : 

```js
    let j = 0; j < 10; j++
```

Boucle pratique pour parcourire les éléments d'un tableau, ou pour faire une action un certains nombre de fois. 

### Action dans un tableau

```js
const notes = [20, 5, 18, 13];
    for( let j = 0; j < notes.length; j++){
      console.log(notes[i]);
    }
```

Ici on vas donc parcourir l'ensemble de notre tableau de notes j'usqu'à la fin. 

Mais aujourd'hui on peut faire la même chose avec une autre sorte de boucle for. 


## Pour dans / for in

Manière plus simple et raccourcie de parcourire les indexs. 

```js
const notes = [20, 5, 18, 13];
    for( let j in notes ){
      console.log(notes[j]);
    }
```
On auras alors le même résultat que précédement, mais avec une écriture plus légère. 
On pourras également l'utiliser pour des objets. 

```js
 const notes = {
      a: 1,
      b: 2
    }
    for( let j in notes ){
      console.log(j);
    }
```
'j' vaudras alors 'a' puis 'b' puis ect... Permet ainsi d'accéder à une propriétés. 

## Pour de / for of

'of' permet d'accéder au valeur. Dans notre cas on ne cherceras plus alors l'index avec i mais directement la note de notre tableau 'notes'. 
Ne fonctionne que sur les choses itérables les tableaux. 

```js
const notes = [20, 5, 18, 13];
    const person = {
      firstname: 'jhon',
      lastname : 'Dhoe'
    }
    for( let note of notes ){
      console.log(notes);
    }
```

Mais attention, si on essaye de faire ça un objet (ici person) alors on auras une erreur.

Petits tips ça marche aussi sur les strings. 
on vas pouvoir itérer sur toutes les lettres d'une string par éxemple. 
Une string est comme un tableau de mot, du coup on peut les utilisers dans les boucles. 

```js
const notes = [20, 5, 18, 13];
    const person = {
      firstname: 'jhon',
      lastname : 'Dhoe'
    }
    const greeting = 'Bonjour'
    for( let letter of greeting ){
      console.log(letter);
    }
```

Si on lui demande un for in à la place alors on auras les index de la lettre. 


```js
const notes = [20, 5, 18, 13];
    const person = {
      firstname: 'jhon',
      lastname : 'Dhoe'
    }
    const greeting = 'Bonjour'
    for( let letter in greeting ){
      console.log(letter);
    }
```


## Exercice 1 : 

Créer un algorithm pour demander un chiffre en 0 et 10. 
Si ce n'est pas le cas alors afficher un message d'erreur. 

Si le chiffre n'est pas bon afficher tout les chiffres avant celui écrit. 

```js
 let chiffre = prompt("Entrez un nombre entre 0 et 10");
      if (chiffre > 10 || chiffre < 0) {
        console.log(" Les nombres n'est pas entre 0 et 10");
      } else {
        for (let i = chiffre; i >= 0; i--) {
          console.log(i);
        }
      }
```

## Exercice 2 :

Créer une variable guess qui contient un nombre. L'utilisateur doit alors deviner le nombre. Si le nombre est = à 8 alors un message bravo, sinon cherche encore. 

Si on veut une valeur qui es un nombre on pourras mêtre notre string * 1. 

```js
 let guess = 8; 
      let chiffre
      while(chiffre !== guess){
        chiffre = prompt('Votre chiffre') * 1
        if(chiffre < guess){
          console.log('Plus')
        } else if (chiffre >guess){
          console.log('Moins')
        }
      }
      console.log('Bravo !! Tu as trouvé')
```

### Sortir d'une boucle / Break

Permet de sortir d'une boucle de force, la plus proche. 
Marche autant pour les boucles while que les for. 

```js
 let guess = 8; 
      let chiffre
      while(true){
        chiffre = prompt('Votre chiffre') * 1
        if(chiffre < guess){
          console.log('Plus')
        } else if (chiffre >guess){
          console.log('Moins')
        } else {
            break
        }
      }
      console.log('Bravo !! Tu as trouvé')
```
