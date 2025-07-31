# Chercher des données - avancé

## Sommaire

- [ORDER BY](#order-by)
- [LIMIT](#limit)
- [OFFSET](#offset)
- [GROUP BY](#group-by)
- [HAVING](#having)
- [Les jointures de table](#les-jointures-de-table)
- [Les requêtes imbriquées](#les-requêtes-imbriquées)

## ORDER BY

```sql
SELECT property1, property2, ...
FROM table
WHERE property4 = condition
ORDER BY property3;
```

| comparateur | description                                           |
| ----------- | ----------------------------------------------------- |
| ASC         | ascending => sens croissant (comportement par défaut) |
| DESC        | descending => sens décroissant                        |

## LIMIT

Pour limiter le nombre de résultats obtenus par la requête.

```sql
SELECT property1, property2, ...
FROM table
WHERE property4 = condition
LIMIT 10;
```

Associé à `ORDER BY`, permet d'obtenir la dernière entrée d'une table :

```sql
SELECT property1, property2, ...
FROM table
WHERE property4 = condition
ORDER BY id DESC
LIMIT 1;
```

## OFFSET

Pour démarer le `SELECT` à partir d'un certain nombre d'élément :

```sql
SELECT property1, property2, ...
FROM table
WHERE property4 = condition
OFFSET 10;
```

Ici, la requête ignorera les 10 premiers résultats et remontera tous les suivants.

Associé à `lIMIT`, on pourra paginer les résultats de requêtes :

```sql
--Page 1 :--
SELECT property1, property2, ...
FROM table
WHERE property4 = condition
OFFSET 0
LIMIT 10;

--Page 2:--
SELECT property1, property2, ...
FROM table
WHERE property4 = condition
OFFSET 9
LIMIT 10;

--Page 3 :--
SELECT property1, property2, ...
FROM table
WHERE property4 = condition
OFFSET 19
LIMIT 10;
```

## GROUP BY

Utilisé pour grouper les résultats d'une requête entre une ou plusieurs tables, souvent utilisé avec des aggrégateurs mathématiques. Par exemple : 

*Requête pour savoir de quelles villes viennent le plus les clients d'une applicationn*

```sql
SELECT COUNT(City), City
FROM Customers
GROUP BY City
ORDER BY COUNT(City) DESC
;
```

## HAVING

Il est impossible de faire un `SELECT` après un `GROUP BY`. Donc on utilise `HAVING` :

*Requête pour savoir de quelles villes viennent le plus les clients d'une applicationn, en ne prenant en compte que les villes avec plus de 10 caractères dans leur nom*

```sql
SELECT COUNT(city), city
FROM customers
GROUP BY city
HAVING LENGTH(city) > 10
ORDER BY COUNT(city) DESC
;
```

## Les jointures de table

Permet de récupérer des données de plusieurs tables, liées par une condition :

```sql
SELECT table_a.property1, table_a.property2, table_b.propertyA, table_b.propertyB ... 
FROM table_a 
INNER JOIN table_b ON table_a.id = table_b.table_a_id;
```

| options    | description                                                    |
| ---------- | -------------------------------------------------------------- |
| LEFT JOIN  | au moins la partie gauche de la jointure répond à la condition |
| RIGHT JOIN | au moins la partie droite de la jointure répond à la condition |
| INNER JOIN | les deux parties de la jointure répondent à la condition       |

## Les requêtes imbriquées

Il est possible d'exécuter une requête `SELECT` sur les résultats d'une autre requête `SELECT` :

```sql
--Afficher quels sont les touristes qui font plus de visite que la moyenne :--
SELECT first_name, last_name, total_visits  
FROM guests 
WHERE total_visits > (
    SELECT AVG(total_visits)
    FROM guests
);
```

Ce n'est pas une pratique recommandée car très coûteuse en ressource et en performances.
