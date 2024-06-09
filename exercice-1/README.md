# Exercice 1 : Validation d’acquis

## Réponses aux questions

1. **Qu’est-ce qu’un conteneur ?**
   Un conteneur est une technologie de virtualisation légère qui regroupe une application et ses dépendances afin de garantir son fonctionnement homogène dans différents environnements.

2. **Est-ce que Docker a inventé les conteneurs Linux ? Qu’a apporté Docker à cette technologie ?**
   Docker n'a pas inventé les conteneurs Linux. Docker a rendu les conteneurs plus accessibles et faciles à utiliser en créant une interface simple et des outils pour leur gestion, déploiement et orchestration. Docker a standardisé les conteneurs avec un format d'image unique et a développé un écosystème complet pour supporter leur utilisation.

3. **Pourquoi est-ce que Docker est particulièrement pensé et adapté pour la conteneurisation de processus sans états (fichiers, base de données, etc.) ?**
   Docker est particulièrement adapté pour les processus sans états car il permet de créer des conteneurs légers, isolés et reproductibles qui peuvent être facilement détruits et recréés sans perte de données.

4. **Quel artefact distribue-t-on et déploie-t-on dans le workflow de Docker ? Quelles propriétés désirables doit-il avoir ?**
   L'artefact distribué et déployé est une image Docker. Elle doit être légère, portable, reproductible, et inclure toutes les dépendances nécessaires à l'application.

5. **Quelle est la différence entre les commandes `docker run` et `docker exec` ?**
   `docker run` crée et démarre un nouveau conteneur, tandis que `docker exec` exécute une commande dans un conteneur déjà en cours d'exécution.

6. **Peut-on lancer des processus supplémentaires dans un même conteneur Docker en cours d'exécution ?**
   Oui, on peut lancer des processus supplémentaires dans un conteneur en cours d'exécution en utilisant la commande `docker exec`.

7. **Pourquoi est-il fortement recommandé d’utiliser un tag précis d’une image et de ne pas utiliser le tag `latest` dans un projet Docker ?**
   Il est recommandé d'utiliser un tag précis pour assurer la stabilité de l'environnement de production. Le tag `latest` peut changer et introduire des incompatibilités ou des comportements inattendus.

8. **Décrire le résultat de cette commande : `docker run -d -p 9001:80 --name my-php -v "$PWD":/var/www/html php:7.2-apache`.**
   Cette commande démarre un conteneur en arrière-plan (`-d`) nommé `my-php` à partir de l'image `php:7.2-apache`. Le port 80 du conteneur est mappé au port 9001 de l'hôte (`-p 9001:80`), et le répertoire de travail actuel est monté dans le conteneur à `/var/www/html` (`-v "$PWD":/var/www/html`).

9. **Avec quelle commande Docker peut-on arrêter tous les conteneurs ?**
   `docker stop $(docker ps -q)`

10. **Quelles précautions doit-on prendre pour construire une image afin de la garder de petite taille et faciliter sa reconstruction ?**
   Utiliser des images de base légères, minimiser le nombre de couches dans le Dockerfile, supprimer les fichiers temporaires et les caches après l'installation des dépendances, et tirer parti du cache de construction Docker.

11. **Lorsqu’un conteneur s’arrête, tout ce qu’il a pu écrire sur le disque ou en mémoire est perdu. Vrai ou faux ? Pourquoi ?**
   Vrai, sauf si des volumes sont utilisés pour persister les données, car les données à l'intérieur du conteneur sont éphémères et sont supprimées lorsque le conteneur s'arrête.

12. **Lorsqu’une image est créée, elle ne peut plus être modifiée. Vrai ou faux ?**
   Faux, une image Docker est immuable.

13. **Comment peut-on publier et obtenir facilement des images ?**
   On peut publier des images sur des registres publics comme Docker Hub ou des registres privés. Pour obtenir des images, on utilise la commande `docker pull`.

14. **Comment s’appelle l’image de plus petite taille possible ? Que contient-elle ?**
   L'image la plus petite possible est `scratch`. Elle ne contient rien par défaut, c'est une image de base vide.

15. **Par quel moyen le client Docker communique avec le serveur Docker ? Est-il possible de communiquer avec le serveur via le protocole HTTP ? Pourquoi ?**
   Le client Docker communique avec le serveur Docker via une API, par défaut en utilisant un socket UNIX. Il est possible de configurer Docker pour communiquer via HTTP/HTTPS pour un accès distant.

16. **Un conteneur doit lancer un processus par défaut que l’on pourra override à l'exécution. Quelle commande faut-il utiliser pour lancer ce processus : `CMD` ou `ENTRYPOINT` ?**
   `CMD` définit la commande par défaut qui peut être remplacée lors de l'exécution du conteneur, tandis que `ENTRYPOINT` définit une commande qui sera toujours exécutée. Utilisez `CMD` si vous souhaitez permettre le remplacement de la commande par défaut.
