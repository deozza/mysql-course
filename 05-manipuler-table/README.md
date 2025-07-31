# Manipuler une table

## Sommaire

- [Créer une table](#créer-une-table)
  - [Les types de propriétés](#les-types-de-propriétés)
    - [Les tailles de données](#les-tailles-de-données)
    - [Le cas `CHAR` et `VARCHAR`](#le-cas-char-et-varchar)
    - [Le cas `FLOAT`](#le-cas-float)
  - [Les options pour les propriétés](#les-options-pour-les-propriétés)
  - [La primary key](#la-primary-key)
- [Mettre à jour une table](#mettre-à-jour-une-table)
  - [Supprimer une propriété](#supprimer-une-propriété)
  - [Ajouter une propriété](#ajouter-une-propriété)
  - [Modifier une propriété](#modifier-une-propriété)
    - [Modifier le nom](#modifier-le-nom)
    - [Modifier les options](#modifier-les-options)
- [Renommer une table](#renommer-une-table)
- [Supprimer une table](#supprimer-une-table)
- [Supprimer le contenu d'une table](#supprimer-le-contenu-dune-table)

## Créer une table

**Prérequis :**

Pour pouvoir créer une table, il faut d'abord indiquer au serveur sur quelle base de données on se situe :

```sql
USE database_name;
```

```sql
CREATE TABLE table (
  property1 INT(10) PRIMARY KEY,
  property2 VARCHAR(255) UNIQUE,
  property3 FLOAT(10,2) NOT NULL,
  property4 DATE DEFAULT NOW()
);
```

**Analyse ligne par ligne :**

1. on indique au serveur qu'on souhaite créer une table de nom *table*
2. on rajoute des propriétés dans notre table
  - elles sont définies par leur nom, leur type et leurs options de configuration
6. on termine l'instruction avec un `;`

### Les types de propriétés

| type      | description                             |
| --------- | --------------------------------------- |
| VARCHAR   | chaine de caractères de taille variable |
| CHAR      | chaine de caractères de taille fixe     |
| INT       | nombre entier                           |
| FLOAT     | nombre à virgule flottante              |
| BOOLEAN   | true ou false                           |
| DATETIME  | date et heure                           |
| TIMESTAMP | temps écoule en ms depuis le 01/01/1970 |

#### Les tailles de données

Les données entre `()` indiquent le nombre de caractères maximum que la colonne acceptera lorsqu'on ajoutera des données. Par exemple, avec `INT(3)`, on poura rentrer des chiffres jusqu'à `999`. Avec `VARCHAR(255)`, on pourra rentrer des chaînes de 255 caractères maximum.

Préciser la taille maximal permet 2 choses :

- optimiser l'espace mémoire et donc les performances
- forcer l'ajout d'une certaine catégorie de données

Par exemple, un code postal fait toujours 5 chiffres. Cela fait sens de préciser `INT(5)`. 
Pour des données dont la taille est variable (un prénom, une adresse email, un prix de vente), cela est trop risqué de préciser un nombre maximal de caractères. Admettons qu'on précise `VARCHAR(50)` pour une adresse email. On ne pourra pas enregistrer de nouveaux utilisateurs qui ont une adresse email trop longue. Dans ces cas, il faut toujours privilégier les limites les plus hautes pour pouvoir gérer le plus de cas possibles.

#### Le cas `CHAR` et `VARCHAR`

Avec `VARCHAR(255)`, on *peut* enregistrer des chaînes de caractères *jusqu'à* 255 caractères. Avec `CHAR(255)`, on *doit* enregistrer des chaînes *de* 255 caractères.

Par exemple, un numéro IBAN fait toujours 27 caractères. On peut donc préciser `CHAR(27)`.

#### Le cas `FLOAT`

Le premier chiffre indique le nombre total de chiffre qu'on peut rentrer, comme avec `INT`. Le second chiffre indique combien de ces chiffres se situent après la virgule, en décimale.

Par exemple, avec `FLOAT(4,2)`, on peut écrire maximum 4 chiffres dont 2 décimales, comme `20.05`. Avec `FLOAT(7,4)`, on peut écrire `999.9999`.

### Les options pour les propriétés

| options        | description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| NOT NULL       | La propriété ne peut être vide                                                |
| UNIQUE         | La valeur ne peut pas être répétée dans la table                              |
| AUTO_INCREMENT | La valeur est un INT qui augmente de 1 à chaque nouvel enregistrement         |
| DEFAULT        | Spécifier quelle est la valeur par défaut si aucune n'est fournie             |
| PRIMARY KEY    | Cette propriété servira d'identifiant pour les enregistrements                |
| FOREIGN KEY    | Cette propriété servira d'identifiant pour les relations avec d'autres tables |

### La primary key

Une clef primaire est un moyen d'identifier une entrée dans une table. Cette option permet également de rapidement accéder à cette entrée si on utilise la propriété associée, car celle-ci sera indexée dans le système. 

Utiliser primary key implique que la propriété associée devra : 

- avoir des valeurs uniques
- être non null

Une table a forcément une et une seule primary key.

## Mettre à jour une table

Pour pouvoir créer une table, il faut d'abord indiquer au serveur sur quelle base de données on se situe :

```sql
USE database_name;
```

### Supprimer une propriété

```sql
ALTER TABLE table
DROP COLUMN nom_colonne;
```

### Ajouter une propriété

```sql
ALTER TABLE table
ADD nom_colonne type_donnees
;
```

### Modifier une propriété 

#### Modifier le nom

Sur des anciennes version de MySQL (5.7 notamment), il faut redéfinir toute la propriété lorsqu'on la renomme :

```sql
ALTER TABLE table
CHANGE nom_colonne nouveau_nom_colonne type_donnees;
```

Sur des versions plus récentes (MySQL 8), il suffit de faire :

```sql
ALTER TABLE table
RENAME COLUMN nom_colonne TO nouveau_nom_colonne;
```

#### Modifier les options

```sql
ALTER TABLE table
MODIFY nom_colonne type_donnees
;
```

## Renommer une table

Pour pouvoir renommer une table, il faut d'abord indiquer au serveur sur quelle base de données on se situe :

```sql
USE database_name;
```

On peut ensuite utiliser :

```sql
ALTER TABLE table RENAME nouveau_nom_table;
```

On peut également utiliser :

```sql
RENAME TABLE table TO nouveau_nom_table;
```

## Supprimer une table

Pour pouvoir supprimer une table, il faut d'abord indiquer au serveur sur quelle base de données on se situe :

```sql
USE database_name;
```

```sql
DROP TABLE table IF EXISTS
;
```

## Supprimer le contenu d'une table

Pour pouvoir supprimer une table, il faut d'abord indiquer au serveur sur quelle base de données on se situe :

```sql
USE database_name;
```

Si on souhaite uniquement supprimer le contenu d'une table (ses données) et conserver sa structure (ses propriétés), on utilisera `TRUNCATE` :

```sql
TRUNCATE TABLE table IF EXISTS
;
```
