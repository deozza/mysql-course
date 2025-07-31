# Syntaxe

## Sommaire

- [Syntaxe](#syntaxe)
  - [Sommaire](#sommaire)
  - [Exemple de script](#exemple-de-script)

## Exemple de script

```sql
SELECT property1, property2
FROM table
WHERE property3='data'
;
```

**Analyse ligne par ligne :**

1. On commence l'instruction par un type d'action à réaliser
2. On indique sur quelle ressource on exécute cette instruction
4. La fin de l'instruction est symbolisée par un `;` (*point-virgule* ou *semi-column*)

Rien n'empêche d'écrire les étapes de l'instruction sur la même ligne :

```sql
SELECT property1, property2 FROM table WHERE property3='data';
```

Mais séparer les étapes de l'instruction sur plusieurs lignes permet de gagner en lisibilité et en compréhension, surtout sur des requêtes plus complexes.

Rien n'empêche également d'écrire les *fonctions* en minuscules :

```sql
select property1, property2
from table
where property3='data'
;
```

Les écrire en majuscule permet de différencier les fonctionnalités du langage SQL des paramètres de la base de données. On gagne en lisibilité et en compréhension.

Dans la requête d'exemple, `data` est entre `''` (*guillemets simples* ou *single quotes*) parce que c'est du texte. Si on voulait écrire des nombres à la place, on aurait pu les écrire directement :

```sql
SELECT property1, property2
FROM table
WHERE property3=42
;
```

Même chose pour des nombres à virgule :

```sql
SELECT property1, property2
FROM table
WHERE property3=3.14
;
```
