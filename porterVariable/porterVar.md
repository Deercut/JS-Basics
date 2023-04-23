# Portée des variables 

Si dans un exemple de code : 

```js
 let age = 18
      if(age >= 18){
        let suffix = 'hello'
      }
      console.log(suffit)
```
La consol vas nous renvoyer une erreur, disant que 'suffit', 
n'est pas définit. 

Ceci est du à la portée de notre varialbe 'suffix'.

La raison est que notre variable n'est déclarée que pour notre bloc courant. C'est à dire qu'étant donné que notre varialbe est déclarée dans le bloc conditionnel (notre if) ça portée est limitée à ce bloc. 

```js
let age = 18
      if(age >= 18){
        let suffix = 'hello'
        console.log(suffit)
      }
```   
Si on mettait notre console.log dans notre bloc condition, alors aucun soucis niveau de la console.        

Si on déclaire notre variable en dehors de notre block conditionnel, alors on pourrait y accéder après et donc on aurais plus le soucis. 

```js
let age = 18
let suffix = 'hello'
      if(age >= 18){
        console.log(suffit)
      }
```   

Par contre si utilisais du vieux code et qu'on remplaçais notre let par un var dans cette exemple 

Alors on aurait pas le soucis, car la portée de var est bien plus grande que let. 

```js
let age = 18
      if(age >= 18){
        let suffix = 'hello'
        console.log(suffit)
      }
```   
Avantage de let et const c'est qu'ils sont beaucoup plus prévisible et donc permet de mieux gérer nos variable. 