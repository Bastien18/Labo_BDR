# Rapport LABO2 BDR
## Loïc Brasey, Bastien Pillonel
### 1.3 Insertion des données
- 1.3.1
Commande :

```
INSERT INTO works_on VALUES('123456789', 3, 10.);
INSERT INTO works_on VALUES('123456789', 5, 10.);
```
L'insertion s'est faite correctement.

- 1.3.2
Commande :
```
DELETE FROM department WHERE dnumber = 5;
```
La suppression à bien eu lieu. La table department n'est pas lié a d'autre table donc tout bon pour delete.

### 1.4 Implémentation des contraintes d'intégrité
- 1.4.3
a) Non l'insertion n'est plus possible cela est tout à fait normal puisque l'on essaie d'insérer des clefs qui font référence sur une les clefs d'une autre tables qui n'a pas encore été peuplée.
b) Desactiver temporairement les contraintes afin de peupler les tables.

