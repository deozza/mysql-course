# Chercher des données

## Sommaire

<!--toc:start-->
- [SELECT ... FROM](#select-from)
- [AS](#as)
- [WHERE](#where)
  - [AND et OR](#and-et-or)
  - [Les opérations mathématiques](#les-opérations-mathématiques)
  - [Les opérations sur chaines de caractères](#les-opérations-sur-chaines-de-caractères)
<!--toc:end-->

## SELECT ... FROM

Syntaxe :

```sql
SELECT table.property1, table.property2, ...
FROM table;
```
Ici, on précise pour chaque propriété de quelle table elle vient. Dans le cas où on ne remonte des propriétés que d'une seule table, on peut s'en passer :

```sql
SELECT property1, property2, ...
FROM table;
```

Si on souhaite faire remonter toutes les propriétés d'une table, on utilisera :

Syntaxe :

```sql
SELECT *
FROM table;
```

## AS

Si on souhaite renommer une colonne dans une requête, on peut utiliser `AS` :

```sql
SELECT property1 AS p1
FROM table;
```

On peut également renommer une table :

```sql
SELECT t.property
FROM table AS t;
```

## WHERE

Syntaxe :

```sql
SELECT property1, property2, ... FROM table WHERE property4 = condition;
```

On n'est pas obligé d'appliquer une clause `WHERE` sur une propriété que l'on remonte avec `SELECT`.

| comparateur  | description                        |
| ------------ | ---------------------------------- |
| =            | vaut exactement                    |
| >            | est strictement supérieur à        |
| >=           | est supérieur ou égal à            |
| <            | est strictement inférieur à        |
| LIKE '%...'  | chaine de caractère finissant par  |
| LIKE '...%'  | chaine de caractère commençant par |
| LIKE '%...%' | chaine de caractère contenant      |
| BETWEEN      | est entre                          |

### AND et OR

Il est possible d'enchaîner plusieurs conditions dans une clause `WHERE`. Pour savoir si ces conditions doivent être appliquées ensembles ou séparément, on utilise `AND` et `OR` :

```sql
CREATE TABLE user(
  id INT PRIMARY KEY AUTO_INCREMENT,
  username VARCHAR(255) NOT NULL,
  date_creation DATE DEFAULT NOW()
);

SELECT *
FROM user
WHERE username LIKE '%xX'
AND id > 100;

SELECT *
FROM user
WHERE date_creation >= '2010-01-01'
OR username LIKE '%10';
```

*On utilise `AND` quand on fait un `BETWEEN` :*

```sql
SELECT *
FROM user
WHERE date_creation BETWEEN '2010-01-01' AND '2010-01-31';
```

Si on souhaite utiliser `AND` et `OR` dans la même clause `WHERE`, il vaut mieux utiliser `()` pour séparer les différentes conditions :

```sql
SELECT *
FROM table
WHERE (property1 = 'condition' OR property1 ='condition2') AND property2 = 'condition';
```

Sans les `()`, MySQL aurait interprété de la manière suivante :

```sql
SELECT *
FROM table
WHERE property1 = 'condition' OR property1 ='condition2' AND property2 = 'condition';


--Interprété en :--

SELECT *
FROM table
WHERE property1 = 'condition' OR (property1 ='condition2' AND property2 = 'condition');
```

### Les opérations mathématiques

| opérateurs                | description                       |
| ------------------------- | --------------------------------- |
| AVG(property)             | moyenne                           |
| MAX(property)             | valeur maximale                   |
| MIN(property)             | valeur minimale                   |
| FLOOR(property, decimals) | arrondi à l'inférieur             |
| CEIL(property, decimals)  | arrondi au supérieur              |
| COUNT(property)           | nombre d'occurences dans la table |

### Les opérations sur chaines de caractères

| opérateurs                                 | description                                        |
| ------------------------------------------ | -------------------------------------------------- |
| LENGTH(property)                           | taille d'une chaine de caractères                  |
| UPPER(property)                            | met la chaîne en majuscule                         |
| LOWER(property)                            | met la chaîne en minuscule                         |
| CONCAT(string1, string2)                   | concatène plusieurs chaînes de caractères          |
| SUBSTR(value, startAt, numberOfCharacters) | Extrait une sous-chaine de caractères d'une chaine |
