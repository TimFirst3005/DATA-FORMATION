*Ceci est un tutoriel que je fais pour presenter de façon succinte Snowflake*

# Architecture, Competitors, and SnowflakeSQL

## C'est quoi Snowflake ?

Snowflake est un entrepôt de données basé sur le Cloud qui utilise un modèle de stockage de données en colonnes.

***Mais qu'est-ce que cela signifie exactement ?***
Pour rappel, un entrepôt de données classique est comme une bibliotèque avec une collection bien organisée de livres, classés en cotégories. De même, il contient et organise les données provenant de différents endroits.
Cependant, plus nous ajoutons de livres, plus nous avons bésoin d'espace et de ressources. C'est le cas pour les entrepôt de données.

Le Cloud permet bien d'avantages, à savoir :
- Evolutivité 
- accéssibilité
- Rapport coût-efficacité
- Diminution des efforts de gestion.

*Parlons maintenant du stockage en colonne*
Contrairement aux BD orientées ligne comme Postrgres qui stockent les informations par ligne, les BD en colonnes ou orientés colonnes stockent les données par colonnes. c.à.d que les informations de chaque colonne sont stockées ensemble.

Sa particularité est que lorsque nous devons mener des analyses, nous ne recupèrons que les colonnes qui nous pertinantes, ci qui rend la repéraction plus éfficace alors qu'avec la BD orientée ligne nous recupérons tous les enregistrements, qui lui est plus optimisé pour les opérations transactionnelles.

Alors, ***Snowflake combine la puissance de la technologie cloud, l'entreposage de données et le stockage de données en colonne pour fournir une solution puissante et évolutive pour l'analyse des données***.

Conçu pour le cloud, il offre une évolutivité et une flexibilité élevées. En organisant les données en colonnes, les requètes s'exécutent beaucoup plus rapidement, permattant ainsi des performances et une efficacité améliorées.

Il a une capacité unique à se connecter à plusieurs fournisseurs de cloud tels AWS, Google Cloud Plateform ou Azure.

Les entreprises l'utilisent largement pour des analyses avancées et le BI, permettant une prise de décision basée sur les données.


Avec Snowflake, nous pouvons stocker, transformer et gérer éfficacement les grands ensembles de données. De plus, il excelle dans l'intégration et l'analyse transparente de diverses sources de données.
Aussi, les possibilités de partages de données permettent de faciliter la collaboration et l'échange de données entre différentes équipes et organisations.

Avec sa large gamme de fonctionnalités, il devient un atout  indispensable pour les organisations à la recherche de solutions complètes de gestion de données.


## Architecture

Avant de parler de l'architecture, parlons du stockage et du calcul, ou de la manière dont les données sont stockées et traitées.

##### Disque partagé et sans partage
Traditionnellement, de nombreuses bases de données suivent une architecture "Disque partagé", comme suit.
![alt text](image-3.png)

Sur l'image de gauche, chaque noeud (pensez à un processeur ou un ordinateur) possède sa propre mémoire et son propre CPU, mais ils partagent le même stockage, permettant à n'importe quel noeud de lire ou d'écrire sur n'importe quelle partie du stockage partagé.

Sur celle de droite, l'architecture sans partage sépare le stockage et le calcul. Ici, chaque noeud possède son propre stockage. Il s'agit d'un concept clé appelé "**découplage de stockage et du calcul**".
Cela garantit que
- Le stockage et le traitement des données est éfficace 
- Le traitement des données se fait indépendamment
- chaque composant peut fonctionner sans dépendre de l'autre.

Et bien, ***c'est ce concept de découplage qu'adopte Snowflake***. D'ou les véritables avantages
- Evolutivité améliorée
- Snowflake peut stocker beaucoup plus de données et/ou les traiter plus rapidement de manière indépendante
- Et donc, des réponses plus rapides et des opérations plus rentables.

Voici un aperçu des conposants fondemmentaux de l'architecture unique de Snowflake.
![alt text](image-4.png)
Il est aussi important de noter que Snowflake utilise une architecture hybride. C.à.d qui bien qu'il dispose d'une couche de stockage partagée centralisant toutes les données, son informatique est nettement découplée.

*Essayons d'examiner chaque couche.*
* **La couche de stockage - Storage Layer**

Lorsque les données sont chargées dans Snowflake, il les organise dans un format de stockage en colonnes, ce qui lui permet une recupértion et une analyse éfficaces des données comme nous l'avons mentionner plutôt.
De plus, Snowflake s'occupe de toutes les optimisations et compressions internes, ce qui signifie qu'il organise et réduit automatiquement la taille de nos données pour en faciliter l'accès et l'analyse. Pas besoin de le faire manuellement.

Cette couche se compose de tables, schémas et de bases de données, fournissantune organisation structurée à nos données. Cela facilite la gestion et la récupération des informations dont nous avons bésoin.

* **La couche de calcul - Compute Layer**

C'est l'endroit où les requètes sont traitées et transformées en informations précieuses.
C'est en fait la salle des machines de Snowflake :smile:, où toute la magie opère! 
Snowflake utilise ce qu'on appelle des entrepôts virtuels pour y parvenir. Ce sont des ressources informatiques temporaires créées lorqu'on soumet une requète. On peut les considérer comme des ordinateurs spécialement conçu pour gérer le traitement des requètes.
Ces entrepôts virtuels peuvent être agrandis ou reduits selon les besoins : **évolutivité**.
Ils sont conçu pour des performances optimales donc ils fournissent des resultats de requètes rapides : **Performances**.
Nous payons uniquement pour les entrepôts virtuels que nous utilisons afin d'économiser de l'argent sur mes coûts d'entrposage des données.


- **Les services Cloud - Cloud Services Layer**

Celle-ci garantit que lorsque nous exécutons une requète, les bonnes ressources, le calcul et le stockage sont alloués éfficacement pour obtenir des résultats plus rapides.
Il est également chagé de maintenir la sécurité de nos données et de contrôler l'accès aux données.
Essentiellement, cette couche agit comme le chef d'orchestre, coordonant tous les aspects de Snowflake pour offrir une expérience utilisateur fluide, sécurisée et fiable.


## Des Alternatives de Snowflake

Voyons, avant de continuer notre exploration, des solutions similaires et comment Snowflake se compare à elles.

**Solutions similaire**
Aux titre des solutions similaires, nous pouvons citer *Google BigQuery*, *Amazon REDSHIFT* et *Databrics* qui sont des plateformes de données des trois(03) grands fournisseurs de cloud. Nous parlerons également de PostgreSQL qui est un SGBDR en essayant de mieux comprendre ses différences par rapport à Snowflake.


**Fonctionalité** | **Snowflake** | **Google BigQuery** | **Amazon REDSHIFT** | **Databrics** | **PostgreSQL** |
|:----------------|:-----------------|:-----------------|:------------------|:-------------------|:------------------|
|**Architecture** | Dissocie le stockage et le calcul|Dissocie le stockage et le calcul|Peut associer ou dissocier le stockage et le calcul en fonction du cluster choisi|Dissocie le stockage et le calcul|PostgreSQL suit une architecture monolithique qui regroupe toutes les fonctionalités|
| **Evolutivité** | évolution rapidement automatique, en ajustant le processeur, la mémoire et le stockage adapté aux demandes de charges de travail, garantissant performence et rentabilité.| évolution automatique|évolution automatique lente|évolution automatique|nécessite une mise à l'échelle manuelle|
|**Gestion**|Nécessite moins d'effort de gestion|Nécessite moins d'effort de gestion| Nécessite plus d'effort de gestion|Nécessite plus d'effort de gestion|Nécessite plus d'effort de gestion|

Toutes ces solutions fournissent des contrôles d'accès et garantissent la sécurité et la confidentialité des données.
Elles proposent également le cryptage pour garantir que les données rentent protégées. Cependant chacune dispose de moyens différents  pour y parvenir.
Elles disposent toutes d'un support de données semi-structurées (JSON, Avro, Parquet, CSV)

DataBrics, en plus, prends également en charge les données non structurées telles que le texte, les images et l'audio.

**Intégration et facturation**

**Fonctionalité** | **Snowflake** | **Google BigQuery** | **Amazon REDSHIFT** | **Databrics** | **PostgreSQL** |
|:----------------|:-----------------|:-----------------|:------------------|:-------------------|:------------------|
|**Intégration avec les fournisseurs de solutions cloud**| Prend en charge le multi-cloud nativement|Prend en charge le multi-cloud et plusieurs connecteurs|Single cloud, il est hébergé dans son propre écosystème| Prend en charge le multi-cloud nativement| Postgres peut être déployé sur plusieurs plateformes cloud|

La plupart des fournisseurs de cloud proposent différement les tarifs de calcul et de stockage; certaines par secondes et d'autres par emplacement, c'est à dire par processeur virtuel utilisé pour exécuter des ressources.
PostgreSQL, particulièrement, est open source mais les prix varient en fonction du fournisseur d'hébergement.

Encore une fois, ce qui rend Snowflake unique, c'est architecture de calcul et de stockage découplée qui le rend idéal pour les charges de travail nécessitant beaucoup de traitement de données ou qui doivent évoluer rapidement. Il permet un partage sécurisé de données entre organsations, departement ou utilisateurs, garantissant la confidentialité et l'intégrité des données

Il offre une interface conviviale avec une faible courbe d'apprentissage, ci qui  le rend facile à utiliser. Cela en fait une bonne optionpour les organisations qui decouvrent les entrepôts de données.

***SnowflakeSQL et PostgreSQL sont-ils similaires ?***
**Oui**, ils sont tous les deux assez similaires.
Snowflake suit le code SQL de l'Américan National Standards Institute(ANSI), ce qui signifie que si nous connaissons PostgreSQL, nous pouvons rapidement commencer à utiliser SnowflakeSQL.

# Snowflake SQL et ses concepts clés

#### Connexion à Snowflake et Commandes DDL

Ici, nous explorerons différentes methodes de connexion à Snowflake et présenterons les commandes DDL de base de Snowflake.

##### Connexion
Il existe différentes façon de se connecter à Snowflake. L'une des options les plus conviviales est l'interface Web Snowflake, souvent appelée Snowsight. Il vous suffit simplement de vous inscrire en créant un compte et commencer à explorer.
Snowflake propose des Worksheets(feuilles de travail) pour créer et exécuter des requètes.

Snowflake prend également en charge des 
- connexions via les pilotes **ODBC**(**O**pen **D**atabase **C**onnectivity) et **JDBC** (**J**ava **D**atabase **C**onnectivity). Ceux-ci permettent à des outils tels que DB Visualizer et Tableau d'accéder aux Bases de Données de Snowflake
- Connecteurs spécialement conçus pour les langages tels que Python, Spark et plus afin d'améliorer l'intégration de Snowflake.


**SnowSQL**
SnowSQL est un autre moyen de se connecter directement à son compte Snowflake à l'aide de de la ligne de commande.
Pour l'utiliser, il faut l'installer. Il propose des version pour Linux, Windows et Mac.

***Parlons maintenant du staging de Snowflake***
C'est en quelque sorte une zone d'attente où les fichiers de données sont temporairement stockés avant d'être chargés dans les tables principales.
Lorsque les données sont stockées dans Snowflake, on parle de **staging interne**; si elles sont stockées sur des plateformes externes comme Amazon S3 ou Google Cloud Storage, on parle de **staging externe**.

Les données brutes, comme un fichier CSV, entrent d'abord dans cette zone de staging. Ensuite, sont chargées dans les tables de la bases de données.
![alt text](image-5.png)


##### Les Commandes DDL(Langage de Définition des Données)

Elles sont utilisées pour définir et gérer la structure d'une base de données comme  créer des tables ou définir des relations (CREATE, ALTER, DROP, RENAME, COMMENT)
Elles sont toutes presque similaires dans l'utilisation.

### Structure des Bases de Données et DML

*Ici, nous explorerons les différents objets dans Snowflake et un aperçu des commandes DML*

SHOW, DESCRIBE, INSERT, UPDATE, MERGE, COPY.

##### Structure
Les commandes INSERT, UPDATE et MERGE sont similaires à celles de PostgresSQL

**Explorons chacune**
- SHOW permet d'afficher et donner des informations
- DESCRIBE ou DESC permet d'obtenir des infomations plus détaillées

**Commandes DML(Data Manipulation Language)**
- INSERT: Snowflake permet d'inserer le resultat d'une requète dans une table.
- UPDATE pour mettre à jour les donnéesg
- MERGE permet la fusion des données de deux tables, ce qui est utile pour synchroniser des tables similaires.
- COPY INTO permet de charger les données d'un fichier ou d'une étape spécifié dans une table Snowflake.


### Type de Données et Convertion des Type de Données dans Snowflake.

**Types de Données**
Voici une liste de types de données courants dans Snowflake : 
*VARCHAR, NUMERIC, INT, DATE, TIME, TIMESTAMP*. Il y'a également VARIANT qui est très puissant pour stocker les données semi-structurées.

Certains types sont identiques à ceux de Postgres à quelques différences près tels :
- *VARCHAR* a une longueur max de 16.777.216 dans snowflake contre 65.535 dans Postgres
- *NUMERIC* a une longueur de 38 pour snowflake contre 37 pour Postgres, ce qui a un impact sur le nombre de chiffres stockés avant et après la virgule.
- *INTEGER*: la portée de snowflake dépasse de loin celle de Postgres.

- *DATE* : Snowflake prend en charge plusieurs formats dont celui par defaut est `YYYY-MM-DD`
- *TIME* : Snowflake capture les heures au format `HH-MI-SS`
- *TIMESTAMP* pour une fusion de DATE et TIME dans un seul champ de notre table

**Conversion**
Snowflake propose plusieus méthodes de conversion 
- CAST(Donnée_à_convertir AS type_cible)
- Donnée_à_convertir `::` type_cible
- Il est aussi possible d'utiliser le TO_TPYE_CIBLE. Par exemple TO_DATE(Données_à_convertir)


### Fonctions, Tri et Regroupement

Dans snowflake comme dans Postgre, nous retrouvons presque les même fonctions, les mêmes Clauses pour les tris et regroupement. 
Pour le groupement, Snowflake propose une nouvelle clause qui est `GROUP BY ALL`. Celle-ci permet de grouper les resultats de nos requètes par toutes les colonnes énumérées dans la clause SELECT et donc d'éviter d'énumérer plusieurs colonnes dans le `GROUP BY` habituelle comme dans Postgres.


# Concepts Avancés DE Snowflake SQL

*Ici nous aborderons quelques concepts avancés de Snowflake SQL*

### Les Jointures
`INNER JOIN`,
 `OUTER JOIN` (`LEFT JOIN` ou `LEFT OUTER JOIN`, `RIGHT JOIN` ou `RIGHT OUTER JOIN`, `FULL JOIN` ou `FULL OUTER JOIN`), 
 `CROSS JOIN` 
 et `SELF JOIN`

*Nous aborderons plus spécifiquement les jointures dites naturelles et latérales.*
`NATURAL JOIN` et `LATERAL JOIN`
Nous savons déjà que les jointure sont un moyen de combiner les données de plusieurs tables.
Les mécanismes de jointure dans Snowflake sont les même que celles dans le SGBDR PostgreSQL.

**NATURAL JOIN**
Contrairement aux jointures standard, le `NATURAL JOIN` élimine les colonnes en doubles en faisant automatiquement correspondre les colonnes portant le même nom pendant qu'avec un `JOIN` standard les colonnes portant les mêmes noms se repètent.

Voici la syntaxe:
```
SELECT ...
FROM <première table> [
                    {
                        |NATURAL [ { LEFT|RIGHT|FULL } [OUTER ] ]
                    }
                   ]JOIN <deuxième table>
[ ... ]
```

**LATERAL JOIN**
C'est une fonctionnalité SQL puissante qui apporte plus de flexibilité à nos requêtes. Elle permet à une sous requête dans la clause FROM d'acceder aux colonnes d'une table ou d'une vue précédente. Ainsi, lorque nous utilisons `LATERAL`, la sous-requête de droite peut faire référence à des colonnes de la table de gauche, ce qui rend les requêtes plus dynamiques.

Syntaxe : 
```
SELECT ...
FROM <left_hand_expression> , -- 
LATERAL
(<right_hand_expression>)
```
Un des avantages est qu'il nous évite les requêtes avec plusieurs JOIN qui ralentissent  considérablement la requête et augmentent les coûts de calcul.

Nous aborderons les techniques de reduction des coûts par la suite.


### Sous-requêtes et CTE

**Sous-requête**
Comme nous le savons déjà, c'est une requête imbriquée dans une autre, couramment utilisée dans les clauses FROM, HAVING, WHERE ou SELECT pour affiner les resultats ou analyser les données.
Snowflake prend en charge les sous-requêtes corrélées et les non corrélées.

**Pour rappel**, une sous-requête corrélée fait référence aux colonnes de la requête externe ou principale et une sous-requête non corrélée fonctionne indépendamment de la requête principale.

Bien que Snowflake soit robuste, il presente quelques limites en ce qui concerne les sous-requêtes. Il ne prends pas en charge l'utilisation de `LIMIT` dans une sous-requête corrélée.

**CTE - Common Table Expressions**
Lorsque les sous-requêtes deviennent complexes et comportent de nombreuses conditions, nous avons besoin d'une approche plus propre et plus flexible. C'est là que les CTE s'averent utiles.
Le CTE, pour simplifier, c'est le fait de donner un surnom à une requête afin que nous puissions l'utiliser dans une autre requête en y faisant référence comme tout autre table.


### Optimisation de requêtes dans Snowflake

L'optimisation d'une requête consiste à transformer une requête en une version plus éfficace.
Nous savons que la couche des Services Cloud de Snowflake dispose d'un moyen d'optimisation des requêtes. Cependant, la manière dont nous redigeons nos requêtes compte également. Une requête bien structurée permet à Snowflake de l'optimiser plus éfficacement.
L'éfficacité ici signifie deux(02) indicateurs clés : la rapidité et le coût. Et donc, une requête optimisée donne des resultats plus rapides, ce qui permet de gagner du temps. En ce qui concerne le coût, des temps de requêtes courts dans Snowflake permettent d'économiser de l'argent.


***Quelques problèmes courants susceptibles de la ralentir les requêtes***
- **Les jointures**: l'un des principaux responsables est l'explosion des jointures qui se produit lorsque nous oublions de specifier les conditions de jointure. Cela peut créer un produit cartésien, conduisant ainsi à des resultats nettement plus importants.
- **UNION au lieu de UNION ALL** : Le fait d'utiliser UNION alors que UNION ALL peut faire l'affaire. UNION supprime les doublons mais cela prend plus de temps à le faire. Et donc, si nous sommes sûr que nos données ne contiennent pas de doublons, utiliser UNION ALL pourrait produire des resultats plus rapides.
- **Filtres et Limites** : l'utilisation des filtres et des limites peut produire des resultats plus rapides et plus rentables lorsqu'il s'agit  de grands ensembles de données.
- **Filtres avant jointure** : Appliquer les filtres avant les jointures via l'uilisation des CTE permet de gagner en efficacité (rapidité et economie en ressources).


### Gestion des données semi-structurées

Après, maitrisé le sujet de l'optimisation de nos requêtes, nous plongeons maintenant dans la gestion des données semi-structurées.

Bien que les données semi-structurées n'aient pas de structure définitive comme celle structurées, elle offrent une flexibilité.

L'un de ces types de données est le JSON pour JavaScript Object Notation, un format de données couramment utilisé dans les API, le developpement d'applications et les fichiers de configuration. Il est au format `Clé : Valeur`.
Une bonne nouvelle est que Snowflake prend en charge nativement le JSON; il dispose de fonctionalités intégrées pour stocker, traiter et intéroger efficacement des fichers de données JSON.
A titre de comparaison, Postgres gère les données JSON en utilisant le type de données `JSNOB`, tandis que Snowflake utilise le type de données `VARIANT`. Le type `VARIANT` prend charge  à la fois les données d'objet(*paires `Clé : Valeur`*) et de tableau(*liste ordonnée de valeurs*).

***Voyons comment travailler avec les données semi-structurées comme JSON***
- **`PARSE_JSON`** est une fonction qui permet de convertir les chaines au format JSON en type VARIANT en renvoyant un objet JSON valide, ce sui simplifie la façon dont nous stockons et intérrogeons les JSON.
- **`OBJECT_CONSTRUCT`** est une fonction qui prend des paires clé-valeur et renvoie un objet JSON.


***Comment intérroger une colonne de données JSON***

- `:` Permet de recupérer les valeurs de clés spécifiques d'une colonne contenant une données au format JSON. (par exemple `nom_colonne:clé`)
- `:` ou `.` permet de recupérer les valeurs imbriquées dans le JSON. (par exemple `colonne:clé_niveau1:clé_niveau2:clé_niveau3` ou `colonne:clé_niveau1.clé_niveau2.clé_niveau3`).


