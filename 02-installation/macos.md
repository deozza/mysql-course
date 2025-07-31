# Installation sur MacOS

**Prérequis** :

- avoir accès au terminal bash
- avoir installé [brew](https://brew.sh/fr/)

## Étape 1 : installer MySQL

```bash
brew install mysql
```

## Étape 2 : activer le serveur

```bash
brew services start mysql
```

## Étape 3 : créer le mot de passe root

```bash
mysqladmin -u root pasword 'nouveaumotdepasse'
```

## Étape 4 : vérifier l'installation

```bash
mysql -u root -p
```

Rentrer le mot de passe renseigné à l'étape 3. Le terminal devrait ensuite ouvrir une connexion au serveur MySQL.
