# Rapport LABO2 BDR
## Loïc Brasey, Bastien Pillonel
### 1.2 Implémentation des tables sous PostgreSQL
Voici le code pour implémenter notre schéma nous avons juste commenter les deuxièmes primary key de certaines tables comme nous n'avons pas encore ajouter les contraintes d'intégrité referentielle.
```
CREATE schema compagny;

set search_path to compagny;

create table employee
(
    fname     varchar(15) NOT NULL,
    minit     char(1),
    lname     varchar(15) NOT NULL,
    ssn       char(9)     NOT NULL PRIMARY KEY,
    bdate     date,
    address   varchar(30),
    sex       char(1),
    salary    decimal(10, 2),
    super_ssn char(9),
    dno       integer     NOT NULL
);

create table department
(
    dname          varchar(15) NOT NULL,
    dnumber        integer     NOT NULL PRIMARY KEY,
    mgr_ssn        char(9)     NOT NULL,
    mgr_start_date date        NOT NULL
);

create table dept_locations
(
    dnumber   integer NOT NULL PRIMARY KEY,
    dlocation integer NOT NULL /*PRIMARY KEY*/
);

create table project
(
    pname     varchar(15) NOT NULL,
    pnumber   integer     NOT NULL PRIMARY KEY,
    plocation integer,
    dnum      integer     NOT NULL
);

create table works_on
(
    essn  char(9)       NOT NULL PRIMARY KEY,
    pno   integer       NOT NULL /*PRIMARY KEY*/,
    hours decimal(3, 1) NOT NULL
);

create table dependent
(
    essn           char(9)     NOT NULL PRIMARY KEY,
    dependent_name varchar(15) NOT NULL /*PRIMARY KEY*/,
    sex            char(1),
    bdate          date,
    relationship   varchar(8)
);

create table location
(
    lnumber integer     NOT NULL PRIMARY KEY,
    lname   varchar(15) NOT NULL
);

```

### 1.3 Insertion des données

