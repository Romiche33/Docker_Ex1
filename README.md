Exercice 1 - Dockerization d'une application web
Objectif
L'objectif de cet exercice est de dockeriser une application web à l'aide d'un Dockerfile et d'un docker-compose.yml.

Instructions
1-Cloner le repository GitHub : Clonez le repository GitHub fourni dans l'énoncé de l'exercice.

2-Créer un fichier Dockerfile : Créez un fichier nommé "Dockerfile" (sans extension) à la racine du projet.

3-Contenu du Dockerfile : Le Dockerfile doit être basé sur une image existante contenant les outils nécessaires à l'exécution de l'application (PHP et Apache). Vous pouvez utiliser l'image PHP avec Apache de la version 7.4 comme point de départ. Le contenu du Dockerfile est le suivant :

FROM php:7.4-apache
COPY . /var/www/html/

4-Construire l'image Docker : Construisez l'image Docker en exécutant la commande suivante dans le répertoire du projet :
docker build -t rcreisse-exo1 .

5-Instancier l'image Docker : Instanciez l'image Docker en utilisant le fichier docker-compose.yml fourni. Assurez-vous que le port 8090 de l'hôte est mappé sur le port 80 du conteneur.

version: '3'

services:
  web:
    image: rcreisse-exo1
    ports:
      - "8090:80"
    volumes:
      - .:/var/www/html
    restart: always

6-Accéder à l'application : Une fois l'image instanciée, ouvrez un navigateur et accédez à l'adresse http://localhost:8090. Vous devriez voir l'application exemple se charger.
