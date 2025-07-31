# Installation sur Linux

**Prérequis** : avoir accès au terminal bash

## Étape 1 : mettre à jour les dépendances

```bash
sudo apt-get update -y && apt-get dist-upgrade
```

## Étape 2 : installer les paquets MySQL

```bash
sudo apt-get install mysql-server
```

## Étape 3 : sécuriser l'accès

```bash
sudo mysql_secure_installation
```

Suivre les étapes à l'écran

## Étape 4 : activer le serveur

```bash
sudo systemctl start mysql
```

## Étape 5 : vérifier l'installation

```bash
mysql -u root -p
```

Rentrer le mot de passe renseigné à l'étape 3. Le terminal devrait ensuite ouvrir une connexion au serveur MySQL.
