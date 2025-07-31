# Mettre à jour les données

Syntaxe :

```sql
UPDATE table
SET property1 = value
;
```
Si on souhaite mettre à jour les données de certaines entrées en particulier, on peut utiliser une clause `WHERE` :

```sql
UPDATE TABLE
SET property1 = value
WHERE property2 > condition
AND property3 = condition
;
```
