## Les formes Normales

Ce sont des règles qui permettents de normaliser nos données dans une BD.

* ***1NF***

> Chaque enregistrement doit être unique et chaque céllule doit contenir une valeur.

* ***2NF***

> En plus de satisfaire 1NF, si la clé primaire est colonne alors la table est 2NF. 
Si la clé primaire est composite, alors chaque colonne non-clé doit dependre de toutes les clés

* ***3NF***

> En plus de satisfaire 2NF, Elle n'autorise pas les dépendances transitives. Ce qui veut dire que les colonnes de clé non primaire ne peuvent pas dépendre d'autres colonnes de clé non primaire.

Une BD qui n'est pas suffisament normalisée est sujette à trois(03) types d'erreurs d'anomalie : Update, Insert et Delete.



 ## Les Vues
 
 * Creation d'une vue
 ````
 CREATE VIEW nom_de_la_vue AS 
      Instructions de la requete 
      '''
      '''
````
* Mise à jour d'une Vue

Deux options s'offrent. Soit on supprime la vue et on crée ensuite une nouvelle.
La requete suivante permet de supprimer une vue

```
DROP VIEW nom_de_la_vue [CASCADE | RESTRICT]
```
Soit on fait un deux en un
```
CREATE OR REPLACE VIEW nom_de_la_vue AS nouveau_nom_de_la_vue
```
Mais attention dans ce cas il y'a des exigences; la nouvelle requete doit impérativement contenir les mêmes nom de colonnes que l'ancienne et dans le même ordre, elle pourra ensuite ajouter des colonnes supplementaire.


# Les Roles et Controles d'accès

## Les roles 
Ils sont utilisés pour gérer les autorisations d'accès à la BD.
Un role de base de données est une entité qui contient des informations qui :
- définissent des privilèges comme la *`connexion`*, *`création des BD`* et bien d'autres. 
- interagissent avec le système d'authentification client, comme le mot de passe du role en question.

**Syntaxe de création d'un rôle**

`CREATE ROLE nom_du_role;`

Tel qu'écrite, nous n'avons pas défini ce dont est capable de faire ce rôle. Certaines actions peuvent être définies lors de la création.

Les parametres suivants peuvent être définis en les précédant de **WITH**: 
- **PASSWORD** `'mot_de_pass'` pour definir un MotDePass
- **VALID UNTIL** `'AAAA-MM-JJ'` pour définir la période de validité du rôle.
- **CREATEDB** pour dire qu'il peuT créer une BD

Pour modifier un attribut pour un rôle déjà créé

`ALTER ROLE nom_du_rôle CREATEROLE `


## Les autorisations Utilisateurs

Accorder une autorisation/privilèges à un utilisateur/role

 ````
 GRANT Privilège(s) --> (CREATE, UPDATE, INSERT, DELETE, ....)
 ON Objet   --> (Table, Vue, BD, ....)
 TO role  -->  (Utilisateurs ou groupes d'utilisateurs)
````

Revoquer une autorisation/privilèges à un utilisateur/role 

 ````
 REVOKE Privilège(s) --> (CREATE, UPDATE, INSERT, DELETE, ....)
 ON Objet   --> (Table, Vue, BD, ....)
 FROM role  -->  (Utilisateurs ou groupes d'utilisateurs)
````

Ci-dessous la liste des privilèges pour les rôles dans PostgreSQL

`SELECT`, `INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`, `REFERENCES`, `TRIGGER`, `CREATE`, `CONNECT`, `TEMPORARY`, `EXECUTE`et `USAGE`

Attention !!!

Un rôle peut être défini sur un utilisateur, un groupe ou un autre rôle également.

Pour ajouter un role d'utilisateur ***userRole*** à un groupe ***groupRole***, on écrit GRANT `groupRole TO userRole;`



# Le partitionnement de BD / Database Partitionning

### Pourquoi le partitionnement de BD ?

Lorsque la BD s'agrandit (des centaines de Go), l'exécution des requètes devient lente.
Même lorque nous avons défini correctement les index, elle peuvent devenir si volumineuses qu'elles ne puissent rentrer dans la mémoire.

Et donc, à un moment donné, il est judicieux de diviser une table en plusieurs pétites parties: c'est **le partitionnement**.

Il existe deux(02) types de partitionnement.
- **Le partitionnement vertical** :  il consiste à diviser une table en plusieurs même lorqi'elle est déjà bien normalisée. Dans ce cas on y met les colonnes sur lesquelles l'on requête plus dans une table, sur un support plus rapide et celles sur lesquelles l'on requête très rarement sur un support plus lent.

- **Le partitionnement horizontal** : ici, au lieu de diviser à partir des colonnes, on divise à partir des lignes selon un critère que nous choisissons.

Différents dialectes SQL ont différentes manières de créer des tables partitionnées.

**Syntaxe** :

````
CREATE TABLE nom_table (
      ....
      --- Instruction de création 
)
PARTITION BY RANGE (colonne de partitionnement)

--- Creation des tables de chaque partition
....
....
-- Ajout d'un index à la colonne utilisé pour le partitionnement
CREATE INDEX ON nom_table (nom_colonne);

````

# Intégration de Données / Data Integration

Que se passe-t-il si nos données sont reparties sur différentes BD, formats, technologies ou schémas ? C'est là l'intégration des données entre en jeu.

*`L'intégration de données consiste à combiner des données provenant de différentes sources, formats, technologies pour fournir une vue traduite et unifiée de nos données.`*

Lors de l'intégration de données, il est impératif de considérer les éléments suivants :
- L'objectif final; il nous faut bien definir ceux à quoi les données intégrées serviront.
- Le format dans lequel les données sont stockées dans chaque sources (Postgres, MongoDB, CSV, ...)
- Dans quel format notre modèle de données unfiées doit-il être ?
- à quelle fréquence souhaitons-nous mettre à jour les données ?
- Entrer les transformations

Pour les intégrer, il nous faut : 
- Les transformer : 