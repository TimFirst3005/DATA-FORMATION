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