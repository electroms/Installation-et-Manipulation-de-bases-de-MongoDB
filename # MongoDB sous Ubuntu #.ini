# MongoDB #

## MongoDB est une base de données polyvalente puissante, flexible et évolutive. Il combine la 
## capacité d'évoluer avec des fonctionnalités telles que les index secondaires, les requêtes de 
## plage, le tri, les agrégations et les index géospatiaux. ##
 
### MongoDB c'est quoi ? ###
 
### MongoDB est une base de données orientée document, une base de données orientée document 
### remplace le concept de «ligne» par un modèle plus flexible, le «document». En autorisant 
### l'intégration de documents et de tableaux, l'approche orientée document permet de représenter 
### des relations hiérarchiques complexes avec un seul enregistrement. Cela s'inscrit naturellement 
### dans la façon dont les développeurs des langages orientés objet modernes pensent de leurs 
### données. ###
 
## Installer MongoDB ## 

### Importez la clé publique utilisée par le système de gestion des packages. ###
 
### Depuis un terminal, exécutez la commande suivante pour importer la clé GPG publique 
### MongoDB depuis https://www.mongodb.org/static/pgp/server-5.0.asc : ###
 
wget –qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add server-5.0.asc
 
### L'opération doit répondre par un OK. ###
 
### Pour connaitre la version d'Ubuntu exécutée par l'hôte, ouvrez un terminal ou un shell sur 
### l'hôte et exécutez lsb_release -dc. ###

### L'instruction suivante concerne Ubuntu 20.04 (Focal) pour créer le fichier de liste ###
 
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list/mongodb-org5.0.list

### L'instruction suivante concerne Ubuntu 18.04 (Bionic) ###

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list/mongodb-org5.0.list

### L'instruction suivante concerne Ubuntu 16.04 (Xenial) ###

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list/mongodb-org5.0.list

### Recharger la base de données de packages locale 
### Exécutez la commande suivante pour recharger la base de données de packages locale : ### 

sudo apt-get update 

### Installez les packages MongoDB ###
 
### Vous pouvez installer soit la dernière version stable de MongoDB, soit une version spécifique 
### de MongoDB. 
### Pour installer la dernière version stable, exécutez ce qui suit ###

sudo apt-get install -y mongodb-org
  
### Démarrez MongoDB 
### Vous pouvez démarrer le mongod processus en exécutant la commande suivante : ###
 
sudo systemctl start mongod 

### Vérifiez que MongoDB a démarré avec succès ###
 
sudo systemctl status mongod 
 
### Arrêtez MongoDB ###
 
### Au besoin, vous pouvez arrêter le mongod processus en exécutant la commande suivante ###
 
sudo systemctl stop mongod
 
### Commencez à utiliser MongoDB. 
### Démarrez une mongoshsession sur la même machine hôte que le mongod. Vous pouvez 
### exécuter mongosh sans aucune option de ligne de commande pour vous connecter à 
### un mongod qui s'exécute sur votre hôte local avec le port par défaut 27017. ###
 
mongosh
 
### Travailler avec MongoDB
### Au démarrage, le shell se connecte à la base de données de test sur un serveur MongoDB et 
### attribue cette connexion à la base de données à la variable globale db. Cette variable est le 
### principal point d'accès à votre serveur MongoDB via le shell. 
### Opérations de base avec le shell ###
 
### Pour visualiser les bases de données existantes tester l’une de ces deux commandes : ###

show databases 
show dbs
 
### Création d'une base de données : La commande use permet de créer une nouvelle base de 
### données si elle n'existe pas, autrement elle retourne la base existante. ###
 
use testMgdb 
 
### Création d'une collection: 2 façons de création de collection possible ### 

#### 1. via la commande db.createCollection("macollection")

db.createCollection("macollection")
 
#### 2. On peut aussi créer une collection en insérant un élément dans cette dernière. La 
#### commande suivante permet de créer la collection « books » tout en insérant un élément.
 
db.books.insert({ name: "Atomic Habits", Price: 60, description: "How to build good habit and get rid of bad ones" }) 

### Insérer dans une collection 

### La fonction insertOne ajoute un document à une collection. Par exemple, supposons que nous 
###souhaitons stocker un film. Tout d'abord, nous allons créer une variable locale appelée movie 
### qui est un objet JavaScript représentant notre document. Il aura les clés 'titre', 'réalisateur' et 
### 'année' (l'année de sa sortie): ###
 
movie = {'title' : 'Star Wars: Episode IV - A New Hope','director' : 'George Lucas','year' :1977} 
 
### Ensuite nous allons créer la colection « movies » tout en insérant le document « movie ». pour 
### le faire utiliser la commande suivante : ### 

db.movies.insertOne(movie)
 
### Voir la liste des éléments dans une collection ###
 
db.movies.find().pretty()
 
### Afficher le résultat au format JSON : . pretty() ###
 
### find et findOne peuvent être utilisés pour interroger une collection. Si nous voulons juste voir 
### un document d'une collection, nous pouvons utiliser findOne : ###
 
db.movies.findOne()
 
### La commande suivante exécute une recherche avec la condition année = à 1976 ou directeur = George Lucas ### 

db.movies.findOne({$or:[{"year":1976},{"director":"George Lucas"}]},{"_id":1,"title":1}) 
 
### Modifier un élément ### 

### Si nous souhaitons modifier notre film, nous pouvons utiliser updateOne. 
### updateOne prend (au moins) deux paramètres: le premier est le critère pour trouver quel 
### document mettre à jour, et le second est un document décrivant les mises à jour à effectuer. 
### Supposons que nous décidions d'activer les critiques pour le film que nous avons créé 
### précédemment. Nous devrons ajouter un tableau d'avis comme valeur d'une nouvelle clé dans 
### notre document. ###
 
db.movies.updateOne( {title : 'Star Wars: Episode IV - A New Hope'}, {$set : {reviews: []}}) 

### Pour supprimer une collection, on utilise la fonction drop( ). ###

### Utiliser tout d’abord la commande « show collections » pour visualiser les collections que 
### vous venez de les créer sous la base « testMgdb » ### 

### Supprimer par la suite la collection « macollection » à l’aide de la commande drop ( ) ###

db.macollection.drop ( )
  
### On peut vérifier ensuite que la suppression de la collection. 
### Supprimer un élément ou un document d’une collection 
### Avant de la faire visualiser l’unique document dans la collection « movies » en exécutant la 
### commande ci-dessous : ###
 
db.movies.find()
 
### Supprimer par la suite ce document en utilisant la commande suivante (vous pouvez par la suite 
### tester l’effet de cette suppression) : ###
 
db.movies.deleteOne({title : 'Star Wars: Episode IV - A New Hope'})

### Compte rendu 1 – Compte rendu 1 –MongoDB Manipulations MongoDB Manipulations 
### préliminaires ###
 
#### 1. Sous MongoDB, créer la base de données Alyf ####

use Alif

#### 2. Créer la collection « formation » et insérer les documents suivants ####

db.formation.insert({"title":"fitech","Description":"une description","Competences":["sql","nosql","hadoop"]})
db.formation.insert({"title":"DEVOPS","Description":"une description","Competences":["terraform","aws","k8S"]})
db.formation.insert({"title":"GESTION","Description":"une description","Competences":["Agile","blabla","et reblabla"]}) 

#### 3. Afficher le contenu de la collection « formation » ####

db.formation.find().pretty()

#### 4. Supprimer la formation « GESTION » ####

db.formation.deleteOne({"title":"GESTION","Description":"une description","Competences":["Agile","blabla","et reblabla"]})

