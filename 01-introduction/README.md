# Introduction

## Sommaire

- [Base de données ?](#base-de-données)
  - [Définition](#définition)
  - [Cas d'usage](#cas-dusage)
- [Serveur de base de données ?](#serveur-de-base-de-données)
  - [SQL](#sql)
  - [MySQL](#mysql)

## Base de données ?

### Définition

Selon le Larousse :

> ensemble structuré et organisé de données qui représente un système d'informations sélectionnées de telle sorte qu'elles puissent être consultées par des utilisateurs ou par des programmes

Selon Oracle :

> ensemble d'informations qui est organisé de manière à être facilement accessible, géré et mis à jour. Elle est utilisée par les organisations comme méthode de stockage, de gestion et de récupération de l’informations.

Exemples de base de données dans la vie de tous les jours :

- une bibliothèque
- le cerveau
- un musée
- un frigo
- un tableur (google sheet / microsoft excel)

### Cas d'usage

**Pour une application e-commerce** :

- sauvegarder les produits et leurs descriptions
- sauvegarder les stocks
- sauvegarder les commandes passées

**Pour une messagerie instantannée** :

- sauvegarder les messages passés
- sauvegarder les fichiers envoyés
- sauvegarder les salon de discussion

**Pour un CMS comme Wordpress** :

- sauvegarder les blocs visuels du site
- sauvegarder les images, les vidéos, les fichiers audio
- sauvegarder le contenu des articles de blog

## Serveur de base de données ?

### SQL

- Structured Query Language
  - langage de requête
  - utilisé pour manipuler des bases de données
  - apparu dans les années 1970
  - avantages par rapport aux concurrents ISAM et VSAM :
    - permet de récupérer plusieurs données avec une requête
    - permet de récupérer une donnée sans avoir à spécifier son identifiant

### MySQL

- SGBDR (ou RDBMS)
  - Système de Gestion de Bases de Données Relationnelles
  - un serveur de bases de données
- racheté par Oracle
  - raison pourquoi beaucoup préfèrent aujourd'hui utiliser PostgreSQL ou MariaDB à MySQL
- mis au point en 1995
- respecte les principes ACID :
  - Atomicity : si une partie de la requête échoue, alors toute la requête est annulée
  - Consistency : les données enregistrées doivent être cohérentes avec les règles définies lors de la création de la base
  - Isolation : les requêtes sont exécutées indépendament les unes des autres
  - Durability : les données enregistrées doivent le rester même en cas d'erreur majeure du système
- contrairement à certains sysèmes SGBD (ou NoSQL), comme MongoDB :
  - ces systèmes sont BASE :
    - B : basically ...
    - A : ...available
    - S : soft state
    - E : eventually consistent
  - plus axés sur les performances brutes au détriment de la robustesse du système
