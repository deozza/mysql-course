# Ajouter des données

Syntaxe :

```sql
INSERT INTO table(property1, property2, property3, ...) VALUES ('value1', 'value2', 'value3', ...);
```

On peut ajouter plusieurs lignes en même temps, en séparant les `VALUES` par un `,` :

```sql
INSERT INTO table(property1, property2, property3, ...) VALUES
('value1', 'value2', 'value3', ...),
('value1', 'value2', 'value3', ...),
('value1', 'value2', 'value3', ...),
('value1', 'value2', 'value3', ...)
;
```
Si les colonnes n'ont pas d'option `NOT NULL` ou ont une option `DEFAULT` ou `AUTO INCREMENT`, on peut omettre les valeurs dans l'insert :

```sql
CREATE TABLE users (
  id INT PRIMARY KEY AUTO INCREMENT,
  username VARCHAR(255) NOT NULL,
  date_creation DEFAULT NOW()
);

INSERT INTO users (username) VALUES ('pouet');
```

Dans cet exemple, les colonnes `id` et `date_creation` ont des valeurs générées par défaut, on n'est pas obligé de les préciser manuellement à l'insert.
