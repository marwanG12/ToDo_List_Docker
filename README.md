# ToDo_List_Docker

ToDo List App

L application consiste en une API backend Node.js et une interface frontend React. L API permet de gérer une liste de tâches, où chaque tâche peut être marquée comme terminée (done) ou non terminée (not done yet). Il est également possible d ajouter de nouvelles tâches via un formulaire et de supprimer des tâches.
Fonctionnalités :

    Backend Node.js expose des routes pour gérer les tâches :

        GET /tasks : Retourne la liste de toutes les tâches.

        POST /tasks : Permet d ajouter une nouvelle tâche.

        PATCH /tasks/:id : Met à jour l état d une tâche (done ou not done yet).

        DELETE /tasks/:id : Supprime une tâche.

    Frontend React consomme l API backend pour afficher la liste des tâches, permettre de les marquer comme terminées ou non terminées, ajouter des nouvelles tâches via un formulaire, et supprimer des tâches.

Prérequis

Avant de démarrer le projet, assurez-vous d avoir installé Docker et Docker Compose sur votre machine et d avoir lancé docker Desktop.
Lancer l application avec Docker
1. Cloner ce dépôt

git clone https://github.com/marwanG12/ToDo_List_Docker.git

(Pour info : Nous avons inclus le fichier .env dans le dépôt Git car nous n avons pas réussi à faire remonter le fichier .env de notre backend dans notre configuration Docker Compose.)

cd docker-todolist-app

2. Lancer Docker Compose

Dans le répertoire racine de votre projet, exécutez la commande suivante pour construire et démarrer les conteneurs Docker :

docker-compose up 


3. Accéder à l application

    Backend (API) : L API backend sera disponible sur http://localhost:5000/tasks.

    Frontend (UI) : L interface frontend sera disponible sur http://localhost:3000.

4. Arrêter les conteneurs

Pour arrêter les conteneurs Docker en cours d exécution, utilisez la commande suivante :

docker-compose down

Structure du Projet

/todolist-app
├── /backend                   # Code de l'API backend (Node.js)
│   ├── /backend/Dockerfile    # Dockerfile pour le backend
│   ├── /backend/server.js     # Code de l'API backend (Node.js)
│   ├── /backend/.env          # Variables d'environnement pour l'API backend
│   └── /backend/routes/tasks  # Routes pour l'API (GET, POST, PUT, DELETE)
├── /frontend                  # Code du frontend (React)
│   ├── /frontend/Dockerfile   # Dockerfile pour le frontend
│   ├── /frontend/src          # Code source de l'interface utilisateur
│   ├── /frontend/public       # Fichiers publics (HTML, images, etc.)
│   └── /frontend/package.json # Dépendances du frontend
├── docker-compose.yml         # Configuration Docker Compose


Quelle est la différence entre build: et image: dans Docker Compose ?

La directive build: dans Docker Compose permet de construire l image Docker à partir d un Dockerfile situé dans le répertoire spécifié, tandis que image: spécifie directement une image Docker préexistante à utiliser sans avoir à la construire.


Quel est l’intérêt d’utiliser un fichier .env dans un projet Docker ?

L utilisation d un fichier .env permet de centraliser et gérer les variables d environnement de manière sécurisée, facilitant la configuration du projet sans exposer de données sensibles directement dans le fichier docker-compose.yml ou dans le code.


Comment les volumes Docker aident-ils à gérer la persistance des données ?

Les volumes Docker permettent de stocker et de gérer les données de manière persistante en dehors des conteneurs, assurant ainsi que les données ne soient pas perdues lors de la suppression ou du redémarrage des conteneurs.

Si vous deviez ajouter un quatrième service (ex : un reverse proxy NGINX), comment l’intégreriez-vous ?

Pour ajouter un reverse proxy NGINX, il faut définir un nouveau service dans le fichier docker-compose.yml en précisant l image NGINX,
puis configurer le fichier de configuration NGINX pour diriger le trafic vers les services appropriés (comme le frontend et le backend) et enfin de lier ce service aux autres services via des réseaux Docker et de configurer les ports exposés.
