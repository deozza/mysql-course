# Manipulation de BDD

## Sommaire

- [Commandes pour manipuler une base](#commandes-pour-manipuler-une-base)

## Commandes pour manipuler une base

**Lister les bases de données du serveur :**

```sql
SHOW databases; 
```

**Créer une base de données :**

```sql
CREATE DATABASE first_database;
```

**Supprimer une base de données :**

```sql
DROP DATABASE first_database
IF EXISTS
;
```

**Se connecter à une base de données :**

```sql
USE <database_name>; 
```
