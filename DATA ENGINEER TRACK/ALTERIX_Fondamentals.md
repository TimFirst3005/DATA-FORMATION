*Ceci est un mémo pour presenter un peu, l'outil d'ingénieurie de données, Alteryx et avoir de bonnes bases.*

# INTRODUCTION A ALTERYX

## Presentation de Alteryx

*Plantons le décor*.

Nous sommes au Lycée DC, une école qui collecte des données  auprès de différents départements, y compris les resultats des examens de ses élèves.
Elle veut obtenir des informations pertinantes à partir des données, et donc elle vous embauche en tent qu'analyste pour l'aider à le faire.

**Le probleme :** 
Vous devez combiner les données de différents departements.
Commençons par les données de test des étudiants et les données pour développer les insights à partager avec la direction de l'école. Les données sont mis à jour mensuellement, l'automatisation est donc une clé.

La direction aimerait également avoir une visibilité sur votre travail.

**La solution :**
Une solution pour resoudre ce problème est **ALTERYX Designer Desktop**.

***Qu'est-ce que ALTERYX Designer Desktop ?***

Il s'agit de l'un des principaux produits proposées par ALTERYX, une plateforme d'édition et analyse de données pour pour les entreprises et particuliers visant à les aider à donner du sens à leur données.

***Mais pourquoi ALTERYX Designer Desktop est-il le bon outil pour vous aider dans votre travail au Lycée DC ?***

Vous pouvez le considerer comme un laboratoire numérique. Vous pouvez y expérimenter différents éléments de données, outils pour explorer vos données et découvrir des insights, un peu comme un scientifique qui expérimente des produits chimiques dans son laboratoire. 

***Alors que faire exactement ALTERYX Designer Desktop ?***


- Il est conçu  pour gérer de grands ensembles de données sans effort et permet aux utilisateur de nettoyer, transformer et analyser des données provenant de diverses sources.

- Il prend en charge diverses sources de données, des bases de données aux plateformes de medias sociaux.
- Il est facile à installer et configurer, ce qui le rend idéal pour une mise en oeuvre au Lycée DC.


***Pourquoi utiliser ALTERYX Designer Desktop et non un autre ?***
- Il se distingue par sa conception glisser-déposer, permettant aux utilisateurs d'effectuer facilement des tâches de données et  de créer des flux de travail. Cela le rend accéssible à tout type d'utilisateur. 
- Il est essentiellement no-code et convivial.
- Il permet également traiter rapidement de grands ensembles de données, accélérant ainsi toutes les taches liées aux données.
- Il est par conséquent utilisé dans divers secteurs, de la santé au commerce de détail, et par divers rôles, notamment ceux de d'analyste de données, consultant BI et bien dautres.

***La principale façon de travailler avec ALTERYX Designer Desktop consiste à créer des flux de travail.***
![Alteryx flow](Alteryx-flow.png)

**Un flux de travail** est un peu comme une recette.
Tout comme une recette vous guide à travers les étapes de preparation d'un gateau, un flux de travail dans Alteryx Dedigner vous guide à travers les étapes de traitement et d'analyse de données.
Traiter et analyser des données dans Alteryx Designer est similaire à la préparation d'un gâteau.

- La première étape, rasembler les ingrédients; Cela revient dans Alteryx à vous connecter aux données.
- Le seconde consiste à utiliser différents ustensiles pour melanger, combiner et modifier vos ingrédients. Alteryx dispose également d'outils qui permettent de preparer et modifier les données.

- Enfin, vous utiliserz des ustensiles pour preparer et cuire votre gâteau. Dans Alteryx également, des outils spécifiquement pour analyser les données produire des insights pertinants.


Ces différents outils utilisés pour créer flux de travail se trouvent dans la palette d'outils, chacun ayant une fonction bien spécifique.
![alt text](<Capture d'écran 2024-07-12 160742.png>)


*Les flux de travail sont facilement automatisable et les processus appliqués sont visibles pour les utilisateur.*


## La Navigation Dans Alteryx Designer Desktop

**Alteryx Designer Desktop** a une interface qui comporte quatre(04) principaux composants utilisés pour créer des flux de travail.
![alt text](<Capture d'écran 2024-07-12 171309-1.png>)

1. **La palette d'outils** : contient tous les outils nécessaires pour importer et gérer des données.

Tous les outils sont divisés en catégories par rapport à leurs fonctions. Chaque catégorie a sa propre couleur et sa propre forme d'outil, ceci pour faciliter la tâche et comprendre le flux de manière global simplement à regarder.


2. **Le Canevas** :  C'est l'endroit où vous pouvez utiliser les outils pour créer un flux de travail afin d'éffectuer les taches de données.
Il existe plusieurs façon d'y ajouter un outil, via:
-  Glisser-déposer l'outil depuis la palette d'outil
- Clic droit de la sourie dans un espace vide du canevas
- Rechercher l'outil dans la barre de recheche(située dans le supérieur droit de la palette d'outil)  et le glisser sur dans le canevas.

3. **La fenètre de configuration** : Permet de configurer chaque outil dans le Canevas afin d'adapter un flux de travail au besoin. Les composants de cette fenètre varient en fonction de l'outil séléctionné. Lorsqu'il y a une erreur dans la configuration d'un outil, vous pourrez constater un "**!**" rouge sur l'outil.

4. **La fenètre de résultats** : Permet, intuitivement, d'afficher les resultats des flux.
