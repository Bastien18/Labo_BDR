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

  a) Non l'insertion n'est plus possible cela est tout à fait normal puisque l'on essaie d'insérer des clefs qui font référence sur les clefs d'une autre tables qui    n'a pas encore été peuplée.
  
  b) Desactiver temporairement les contraintes afin de peupler les tables.
  
 - 1.4.4

    Impossible d'insérer Steve Jobs et le département car chacun a une clé faisant référence à l'autre. Pour résoudre ce problème il faut changer la granularité des contraintes foreign key en referred (attent la fin de la transaction pour valider les contraintes referentielle) ainsi il est possible d'insérer les deux tuples pendant la même transaction, sans contrainte referentielle, et faire la validation après que les deux insertions ait été faîtes.
  
  - 1.4.5
  
    a) Impossible de faire le update car dno a une foreign key constraint et il n'y pas de department numero 7.
  
    b) Impossible à supprimer car works_on a des tuples faisant ref sur ce ssn.
  
    c) Tout bon pour insérer des heures sur le projet 3 mais pour le 5 comme on a ajouter une foreign key et que le projet 5 n'existe pas dans la table project l'insertion est impossible.
  
    d) Viole la contrainte de foreign key de dept_location en faisant ça donc impossible.
  
### 1.5 Affinement des contraintes d'intégrité référentielle

  - 1.5.1 
  
    Lors de la supression d'un superviseur les employés référant sur leur superviseur doivent mettre à jour leur clef super_ssn à null. Pour cela on ajoute à la contrainte de foreign key de super_ssn, mgr_ssn et essn ON delete set null.
  
  - 1.5.2

    Lors de la modification du numéro d'un department, il faut aussi mettre à jour les autre clefs enfants. Pour cela on ajoute à la contrainte de foreign key de dno. dnum et dnumber ON UPDATE CASCADE.

    
