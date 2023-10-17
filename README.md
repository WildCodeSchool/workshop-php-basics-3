# Démarrage

1.  Reprends ton dossier `basics`
2.  Crée un fichier : `functions.php` à la racine du dossier `basics`
3.  Inclus ton fichier `functions.php` dans `index.php`.
4.  Démarre un serveur HTTP.

## Fonction

1.  Crée une fonction nommée `sayHello` permettant d'écrire _"Hello Bulbi"_.
2.  Appelle ta fonction dans ton fichier `index.php` afin de la tester.

## Return

*   Une fonction **ne doit jamais** (sauf cas rare) afficher directement quelque chose (echo, print\_r, var\_dump...).  
    
*   **Une fonction doit retourner une valeur d'un type bien défini.**

En ré-utilisant notre fonction `sayHello()`

1.  Modifie la fonction pour qu'elle **retourne** "Hello Bulbi" plutôt que de l'afficher directement.
2.  Cette fonction ne doit pouvoir retourner que des chaînes de caractère.

## Paramètre

Toujours à partir de ta fonction `sayHello()`

1.  Modifie la en lui ajoutant un paramètre nommé `name` de **type string**
2.  Modifie la fonction pour qu'elle retourne _"Hello \[NAME\]"_
3.  Rend le paramètre `name` **optionnel**. Si rien n'est précisé, ta fonction devra retourner "Hello Bulbi"

## Chifumi

[Comment créer une fonction ?](#comment-créer-une-fonction)

1.  Crée une nouvelle fonction nommée `fight`, cette fonction retournera une chaîne. Cette fonction va nous permettre de faire combattre deux Pokemon l'un contre l'autre.
2.  Elle prendra donc trois paramètres : `pokemon1` de type **string** et `pokemon2` de type **string** et enfin ton tableau contenant la liste des Pokemon par type.
  
Petit rappel :

*   **Type Plante** : Bulbizarre, Mystherbe, Chetiflor
*   **Type Eau** : Carapuce, Stari, Magicarpe
*   **Type Feu** : Salamèche
*   **Type Sol** : Sabelette, Taupiqueur

  
6.  Algo : Le type Feu l'emporte contre le type Plante. Le type Plante l'emporte contre le type Eau. Le type Eau l'emporte contre le type Feu.  
    En prenant cela en compte, cherche à quel type appartient les deux Pokemon fourni en paramètre.
7.  Retourne "\[POKEMON\_NAME\] a gagné contre \[POKEMON\_NAME\]" en remplacant les deux champs par les valeurs des Pokemon gagnant et perdant.
8.  Si les deux Pokemon sont du même type, il y a match nul  
      
    Indice 1 : Il faudra surement d'abord récupérer le type de chaque pokemon afin de trouver le gagnant.  
    Indice 2 : La fonction [in\_array](https://www.php.net/manual/fr/function.in-array.php) te sera sûrement utile.  
      
    
## Bonus

Nous répétons du code lorsque nous voulons récupérer le type de chaque pokemon. La création d'une fonction à réutiliser serait peut être une bonne idée.

![no understanding](fight.jpeg)

## Comment créer une fonction

Par exemple, je dois écrire une fonction qui prend en paramètres un tableau de nombre, et qui me retourne un tableau contenant uniquement les nombres pairs.

Comment écrire cette fonction ?

**Etape 1 : est-ce que ma fonction a besoin d'un nom ?**

1. Oui, le nom m'est déjà donné => Cool, pas besoin de réflechir plus.

2. Oui, je dois en trouver un => Trouver un nom parlant, en rapport avec ce que la fonction doit faire. Si je ne peux pas trouver de nom court qui synthétise la finalité de la fonction, c'est peut être que je veux faire trop de chose à la fois. Je dois peut être réfléchir à redécouper mon code.

3. Non, je déclare une fonction anonyme (en PHP, c'est situation est plus rare que dans d'autres langages).

```php
function getEvenNumbers()
{
    //...
}
```

Ce que tu vois au dessus est le minimum requis pour qu'une fonction soit structurée correctement. Elle ne fait rien (pour l'instant), mais au moins elle ne provoquera pas d'erreur dans ton script.

**Etape 2 : Est-ce que ma fonction a besoin de "valeurs exterieures" pour fonctionner ?**

1. Oui, je vais avoir besoin de paramètres et de leurs types

2. Non, je n'ai pas besoin de paramètres

```php
function getEvenNumbers(array $numbers)
{
    //...
}
```

**Etape 3 : Est-ce que ma fonction a besoin de retourner quelque chose ?**

1. Oui, 2 étapes supplémentaires :
    - De quel type est ma variable ? Définir le type de sortie et si besoin l'initialiser
    - Retourner une nouvelle variable qui va servir de résultat
2. Non, je n'ai pas besoin de variable de resultat

```php
function getEvenNumbers(array $numbers): array
{
    $result = [];
    return $result;
}
```

**Etape 4 : Que fait ma fonction ?**

J'écris dans mon IDE sous forme de commentaire, ou sur un bout de papier, la logique algorithmique que devrait avoir ma fonction afin de satisfaire le besoin. (Ne pas hésiter à indenter, même sur papier !!)

```php
// Step 1 : Déclarer un tableau de "réception",
// Step 2 : Parcourir le tableau passé en paramètre,
// Step 3 : Tester si le nombre parcouru est un nombre pair,
// Step 4 : Ajouter le nombre au tableau de réception le cas échéant,
// Step 5 : Retourner le nouveau tableau.

function getEvenNumbers(array $numbers): array
{
    // step 1
    $result = [];
    // step 2
    for ($i = 0; $i < strlen($numbers); $i++) {
        $num = $numbers[$i];
        // step 3
        if ($num % 2 === 0) {
            // step 4
            $result[] = $num;
        }
    }
    // step 5
    return $result;
}
```