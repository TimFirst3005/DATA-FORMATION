# INTRODUCTION A L'ENTREPOSAGE DE DONNEES/DATA WAREHOUSING

## LES BASES DU DATA WAREHOUSE

### C'est quoi un entrepot de données ?

Il s'agit tout simplement d'un système informatique conçu pour stocker et analyser de grandes quantités de données pour une organisation.

Il rassemble des données provenant de divers domaines d'une organisation. Ensuite, il intègre et stock ces données et les disponibles pour analyse.

Elle est construite dans l'objectif de :
- soutenir les activités de renseignement, tels les KPIs
- conduire la prise de décision organisationnelle, avec l'object de trouver des moyens d'innover en se basant sur les informations tirées des données après analyses.


### Différences Data Warehouse, Data Mart et Data Lake

Les BD utilisent des tables pour stocker des informations de manière structurée avec des lignes et colonnes. Et donc les organisations les utilisent pour stocker leurs différentes transactions; on les appele **BD transactionnelles**.

**Le Data Warehouse** rassemble des données provenant de différents domaines d'une organisation, les intègre et les rend disponibles pour analyse.

**Le Data Mart** est un peu comme le Data Warehouse mais à la difference, il stock les données d'un seul domaine de l'organisation et il est généralement extrait du Data Warehouse.

Le Data Lake, à la différence du Data Warehouse, peut aussi contenir des données non structurées.


### Analyse Organisationnelle de Data Warehouse

#### Cycle de vie d'un Projet de Data Warehouse

**La Planification**

C'est l'étape où l'équipe planifie comment concevoir le Data Warehouse pour repondre aux bésoins de l'organisation qui consiste à 
- colleter des infos pour comprendre les besoins de l'organisation, qui utilisera le Data Warehouse et comment.
- Modéliser les données: il s'agit de planifier en fonction des bésoins de l'organisation sur la façon dont on transforme les données et les intègre. (Data Engineer et Database Admin)

**L'Implementation**

C'est la phase de conception du Data Warehouse
- Conception du processus ETL, consiste à concevoir et construire les pipelines de données qui extraient, transforment et chargent les données des différentes sources dans l'entrepôt de données 
- Developpement de l'application BI, mise en place des outils BI pour interagir avec l'entrepot de données et créer des rapports nécessaires à l'organisation.

**Support/Maintenance - Test & Deployement**

C'est la phase où l'équipe forme les utilisateurs finaux et maintient le warehouse.
- Test les Data Analyst et Scientist testent le système pour confirmer que leurs exigences commerciales sont satisfaites
- Le Data Engineer deploie met l'entrepot de données à la disposition de l'organisation. Après le déploiement, toute modification importante suivra les mêmes étapes à partir de la phase de planification.

#
## ARCHITECTURE ET PROPRIETES DE L'ENTREPÔT

### **Differentes Couches d'un Data Warehouse**

#### **Les couches**

![alt text](image.png)

**N°01 : Data Source**, Celle-ci contenant la source de données
- les fichiers 
- les BD

**N°02 : Data Staging**, C'est là que se trouvent toutes les données pendant la phase de l'ETL. Le processus ETL lui même les met en staging ou temporairement dans des tables afin qu'elles soient pretes à être utilisées dans les étapes ulterieures. Cette couche génère des données prêtes à être stockés.

**N°03 : Data Storage**, Ici, les données sont stockés dans l'entrepôt de données. Il contient également tous les Data Mart utilisés.

**N°04 : Data Presentation**, C'est là que les données sont mis à disposition des utilisateur finaux.
C'est à partir de cette couche que les utilisateurs intéragissent avec les données stockées, que les requêtes sont exécutées pour faciliter l'analyse.
Cette couche comprend également 
- des outils BI, 
- des outils d'EDA
- les requêtes utilisateur directes
