# Projet_8
## Déploiement d'un modèle dans le cloud

Vous êtes Data Scientist dans une très jeune start-up de l'AgriTech, nommée  "Fruits!", qui cherche à proposer des solutions innovantes pour la récolte des fruits.

La volonté de l’entreprise est de préserver la biodiversité des fruits en permettant des traitements spécifiques pour chaque espèce de fruits en développant des robots cueilleurs intelligents.

Votre start-up souhaite dans un premier temps se faire connaître en mettant à disposition du grand public une application mobile qui permettrait aux utilisateurs de prendre en photo un fruit et d'obtenir des informations sur ce fruit.

Pour la start-up, cette application permettrait de sensibiliser le grand public à la biodiversité des fruits et de mettre en place une première version du moteur de classification des images de fruits.

De plus, le développement de l’application mobile permettra de construire une première version de l'architecture Big Data nécessaire.

## Mission:

Vous êtes donc chargé de vous approprier les travaux réalisés par l’alternant et de compléter la chaîne de traitement.

Il n’est pas nécessaire d’entraîner un modèle pour le moment.

L’important est de mettre en place les premières briques de traitement qui serviront lorsqu’il faudra passer à l’échelle en termes de volume de données !

## Contraintes:

Lors de son brief initial, Paul vous a averti des points suivants :

-Vous devrez tenir compte dans vos développements du fait que le volume de données va augmenter très rapidement après la livraison de ce projet. Vous continuerez donc à développer des scripts en Pyspark et à utiliser le cloud AWS pour profiter d’une architecture Big Data (EMR, S3, IAM). Si vous préférez, vous pourrez transférer les traitements dans un environnement Databricks.

-Vous devez faire une démonstration de la mise en place d’une instance EMR opérationnelle, ainsi qu’ expliquer pas à pas le script PySpark, que vous aurez complété : 

	-d’un traitement de diffusion des poids du modèle Tensorflow sur les clusters (broadcast des “weights” du modèle) qui avait été oublié par 	l’alternant. Vous pourrez vous appuyer sur l’article “Distributed model inference using TensorFlow Keras” disponible dans les ressources

	-d’une étape de réduction de dimension de type PCA en PySpark 

-Vous respecterez les contraintes du RGPD : dans notre contexte, vous veillerez à paramétrer votre installation afin d’utiliser des serveurs situés sur le territoire européen 

-Votre retour critique de cette solution sera également précieuse, avant de décider de la généraliser

-La mise en œuvre d’une architecture Big Data de type EMR engendrera des coûts. Vous veillerez donc à ne maintenir l’instance EMR opérationnelle que pour les tests et les démos.

## Livrables :

- Un notebook sur le cloud contenant les scripts en Pyspark exécutables (le preprocessing et une étape de réduction de dimension de type PCA).
- Les images du jeu de données initial ainsi que la sortie de la réduction de dimension (une matrice écrite sur un fichier CSV ou autre) disponible dans un espace de stockage sur le cloud.

Un support de présentation pour la soutenance, présentant :
- les différentes briques d'architecture choisies sur le cloud ;
- leur rôle dans l’architecture Big Data ;
- la démarche de mise en oeuvre de l’environnement Big Data (EMR ou Databricks)
- les étapes de la chaîne de traitement PySpark.

## La mise en place de l'environnement Big Data pour ce projet implique plusieurs étapes :

Choix du fournisseur de cloud: Dans notre cas, AWS a été choisi comme fournisseur de cloud.

Création d'un bucket S3: Le stockage des données est l'un des éléments les plus importants dans un environnement Big Data. Dans ce projet, Amazon S3 (Simple Storage Service) est utilisé pour stocker les images.Création du bucket S3 p8-ms pour stocker ces images.

Création d'un cluster EMR: Amazon EMR (Elastic MapReduce) est utilisé pour exécuter le code Pyspark sur un cluster de nœuds de calcul. La création d'un cluster EMR nécessite la sélection de la version d'EMR, la sélection du type d'instance, la configuration des règles de sécurité et la définition des autres paramètres de cluster tels que le nombre de nœuds.

Configuration du cluster EMR: Une fois le cluster EMR créé, il doit être configuré pour exécuter le code PySpark. Cela est fait en utilisant un script bootstrap qui installe les dépendances requises sur les nœuds du cluster.

Transfert des données sur le bucket S3: Une fois que le cluster EMR est configuré, les données doivent être transférées sur le bucket S3(images/bootstrap). Cela peut être fait en utilisant la commande AWS CLI ou en utilisant l'interface utilisateur graphique d'Amazon S3.

L'environnement Big Data est prêt à être utilisé pour le traitement des images :

Exécution du code PySpark : Après avoir transféré les données sur le bucket S3, le script PySpark peut être exécuté sur le cluster EMR en utilisant JupiterHub (telechargement du script PySpark avec l'upload JupitherHub ou avec aws cli).

En résumé, nous avons déployé sur le cloud une
solution qui permet avec notre script PySpark
d’extraire les caractéristiques de chaque image
avec un algorithme de transfert learning ,
d’effectuer une réduction de dimension (ACP)
sur ces caractéristiques et leur sauvegarde pour
une utilisation ultérieure.

### Référentiel d'évaluation

Identifier les outils du cloud permettant de mettre en place un environnement Big Data

CE1 Vous avez identifié les différentes briques d'architecture nécessaires pour la mise en place d'un environnement Big Data.

CE2Vous avez identifié les outils du cloud permettant de mettre en place l'environnement Big Data conforme aux normes RGPD en vigueur. 

Utiliser les outils du cloud pour manipuler de la donnée dans un environnement Big Data

CE1 Vous avez chargé les fichiers de départ et ceux après transformation dans un espace de stockage cloud conforme à la réglementation RGPD.

CE2 Vous avez exécuté les scripts en utilisant des machines dans le cloud.

CE3 Vous avez réalisé un script qui permet d'écrire les sorties du programme directement dans l'espace de stockage cloud.

Paralléliser des opérations de calcul avec Pyspark

CE1 Vous avez identifié les traitements critiques lors d'un passage à l'échelle en termes de volume de données.

CE2 Vous veillez à ce que l’exploitation des données soit conforme au RGPD. Dans le cadre de ce projet : 

les données sont stockées, et les traitements sont réalisés, sur des serveurs situés sur le territoire européen

CE3 Vous avez développé les scripts s’appuyant sur Spark.

CE4 Vous vous êtes assuré que toute la chaîne de traitement est exécutée dans le cloud.

### Compétences évaluées

Utiliser les outils du cloud pour manipuler des données dans un environnement Big Data

Identifier les outils du cloud permettant de mettre en place un environnement Big Data

Paralléliser des opérations de calcul avec Pyspark
