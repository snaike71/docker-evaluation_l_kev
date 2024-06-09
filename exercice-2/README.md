# Exercice 2 : Projet Web avec Compose

## Partie 1 : Instructions pour démarrer et gérer le projet

### 1. Clonez le dépôt

    ```
    git clone https://github.com/username/docker-evaluation_x_abc.git
    cd docker-evaluation_x_abc/exercice-2
    ```
### 2. Construisez et démarrez les conteneurs

    Pour l'environnement de développement :
    
    ```
    docker-compose --env-file .env.dev up --build
    ```
    Pour l'environnement de production :

    ```
    docker-compose --env-file .env.prod up --build
    ```
    
### 3. Accédez à l'application web

    aller sur http://localhost:8000.

## Partie 2 : Réponses aux questions

2. **Quelle commande faut-il utiliser pour ouvrir un processus bash interactif sur le conteneur de labase de données MySQL ? Donner ensuite les commandes shell à utiliser pour vérifier que la basepar défaut est bien présente ainsi que son contenu initial**

    1. 

        ```
        docker exec -it <container_id> bash
        ```

    2. 
        Ce connecter à MySQL :

        ```
        mysql -udb_client -ppassword
        ```

        Afficher les bases de données :

        ```
        SHOW DATABASES;
        ```
        Vérifier les tables dans la base de données docker_doc :

        ```
        USE docker_doc;
        SHOW TABLES;
        ```
    
        Affichez le contenu de la table article dans docker_doc (qui doit être vide) :

        ```
        SELECT * FROM article;
        ```
    
        Vérifiez les tables dans la base de données docker_doc_dev :

        ``` 
        USE docker_doc_dev;
        SHOW TABLES;
        ```
        Affichez le contenu de la table article dans docker_doc_dev :

        ```
        SELECT * FROM article;
        ```

3. **. Réaliser un dump de la base de données sur votre machine hôte avec mysqldump en executant unecommande supplémentaire sur le conteneur mysql avec docker compose exec sans utiliser lemode interactif (sans ouvrir de session bash au préalable). Stocker le dump dans un fichierdump.sql. Donner la commande pour réaliser cette tâche. Remarque: le conteneur mysqldispose déjà programme mysqldump, inutile de l’installer.**


    ```
    docker-compose exec db sh -c 'exec mysqldump -udb_client -ppassword docker_doc' > dump.sql
    ```

6. **Configurer le fichier Compose pour permettre de développer le script client PHP (le modifier,l’éditer) sans avoir à reconstruire l’image à chaque changement. Indiquer la commande pourrelancer le projet permettant de recharger les sources dès qu’elles changent.**

    ```
    docker-compose up
    ```
    
8. **Est-ce une bonne pratique de placer des données sensibles (password, clés secrètes, etc.) dans desvariables d’environnement comme on le fait ici ? Pourquoi ? Quelle autre option mise à dispositionpar Docker faut-il privilégier pour le faire ?**

    Non, ce n'est pas une bonne pratique car les variables d'environnement peuvent être accessibles de manière non sécurisée. Il est préférable d'utiliser des secrets Docker pour stocker des informations sensibles. Vous pouvez utiliser docker secret pour gérer les secrets de manière sécurisée dans Docker Swarm.
