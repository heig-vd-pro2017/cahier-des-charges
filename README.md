# Cahier des charges

## Contexte et problématique
La musique a une part importante dans toute manifestation (anniversaire, concert, bar, soirée entre amis, etc.). Néanmoins, la musique est souvent gérée par une personne sur un appareil et il devient difficile pour une autre personne de changer la musique ou proposer la sienne.

## Objectif
Nous souhaitons proposer une application de type client-serveur qui permet aux différents utilisateurs de proposer leur propre musique au serveur, qui les jouera sur un système audio au fur et à mesure de l'événement.

## Public cible


## Limitations
Il s'agit ici de développer une application de type client-serveur multi-utilisateur avec interface graphique qui fonctionnera au niveau du réseau local. Il ne s'agit pas de réaliser une application client-serveur qui permettra de proposer de la musique à n'importe quel serveur n'importe où dans le monde. De plus, le serveur ne pourra pas gérer un nombre illimité d'utilisateurs et lira un nombre restreint de formats. L'application ne gérera pas la sécurité au niveau de la communication réseau tel que le spoofing de clients.

## Fonctionnalités importantes
Les fonctionnalités listées ci-dessous, dans l'ordre d'importance, sont nécessaires au bon fonctionnement de l'application.

### Commun aux deux parties de l'application
- Fonction: Démarrage et arrêt corrects du programme
  - Objectif: Préparer les ressources et les nettoyer correctement
  - Description: -
  - Contraintes: -


- Fonction: Droits client-serveur
  - Objectif: Ne pas autoriser des actions interdites de la part des clients au niveau du serveur et inversément.
  - Description:
    - Les clients ne peuvent pas modifier les paramètres du serveur
    - Les serveurs ne peuvent pas modifier les clients
  - Contraintes: -


- Fonction: Notification des actions
  - Objectif: Ne pas laisser les utilisateurs dans le doute de la bonne réalisation ou non des actions qu'ils effectuent
  - Description:
    - Les résultats de toutes les actions effectuées par les utilisateurs doivent être notifiées
    - Les erreurs ou les limitations doivent être notifiées
  - Contraintes: -


### Côté serveur
- Fonction: Paramétrages basiques du serveur
  - Objectif: Donner un nom au serveur
  - Description: Donner la possibilité aux clients de savoir sur quel serveur ils vont se connecter.
  - Contraintes: -


- Fonction: Effectuer une annonce de connexion
  - Objectif: Autoriser les clients à se connecter au serveur
  - Description: Effectue une annonce dans le réseau local pour avertir les clients que le serveur est disponible à recevoir de la musique
  - Contraintes: Se limite au réseau local


- Fonction: Réception de la musique
  - Objectif: Ajouter de la musique sur le serveur
  - Description: Le client transfère une chanson au serveur qui sera ensuite lue. Le client est notifié du résultat.
  - Contraintes:
    - Une chanson ne peut être envoyée qu'une fois sur le serveur
    - \+ voir point "Accepter ou refuser l'ajout de nouvelles chansons"


- Fonction: Lecture des fichiers MP3 et M4A
  - Objectif: Le serveur supporte uniquement les fichiers MP3 et M4A
  - Description: -
  - Contraintes: Seuls fichiers supportés au début


- Fonction: Ajout de la musique à la base de données/système de stockage
  - Objectif: Sauvegarder les chansons pour la liaison entre l'application et le système de stockage
  - Description: Les metadatas (si présentes) ainsi que les données suivantes sont enregistrées dans la base de données:
    - Artiste
    - Titre de la chanson
    - Album
    - Durée de la piste
    - Chemin du fichier
    - Date d'ajout de la piste
    - Date de lecture de la piste
  - Contraintes: Voir le point "Accepter ou refuser l'ajout de nouvelles chansons"


- Fonction: Actions de base sur la musique
  - Objectif: Effectuer des actions sur la lecture de la musique
  - Description: Passer à la chanson suivante, mettre sur pause, arrêter
  - Contraintes: -


- Fonction: Interface utilisateur
  - Objectif: Interface simplifée pour utiliser le logiciel
  - Description: Voir le mockup en annexe
    - Ajout de chansons locales à l'application
    - Récupération des metadatas des chansons et mise en liste de lecture
    - Voir les chansons en cours de lecture (queue de lecture)
  - Contraintes: La fenêtre ne peut pas être redimensionnée


- Fonction: Contrôle du volume de la musique
  - Objectif: Proposer, dans l'application, le réglage du volume
  - Description: -
  - Contraintes: -


- Fonction: Accepter ou refuser l'ajout de nouvelles chansons
  - Objectif: Accepter ou refuser aux clients de mettre de la musique sur le serveur
  - Description: Si le client tente de mettre de la musique alors que les options suivantes sont activées, l'action du client est refusée:
    - Nombre limité de transferts en parallèle entre tous les clients
    - Nombre limité de transferts de chansons par client
    - Limitation du nombre de chansons que le serveur autorise à avoir dans la queue de lecture
    - Limitation selon l'espace disque
    - Limitation selon la taille du fichier envoyé
    - Limitation selon le type de fichier envoyé
  - Contraintes: -


- Fonction: Système de vote
  - Objectif: Permettre aux utilisateurs de changer de chanson ou d'en prioriser une
  - Description:
    - Si un certain poucentage d'utilisateurs souhaite changer de chanson, le programme passe à la suivante
    - Une chanson qui a un vote positif remonte dans la queue de lecture
    - Une chanson qui atteint un nombre trop élévé de votes négatifs est supprimée de la playlist, de la base de données et du système de stockage
  - Contraintes: Un client ne peut voter qu'une fois pour une chanson


- Fonction: Système de favoris/playlist
  - Objectif: Permettre au client de sauvegarder les metadatas des chansons qui lui plaisent dans la base de données locale de ce dernier
  - Description:
    - Une playlist par défaut est créée automatiquement lors de la configuration du serveur et toutes les chansons y sont enregistrées.
    - Si un client souhaite enregistrer une chanson, le serveur lui envoie les metadatas de cette chanson et ces dernières sont enregistrées dans les favoris ou dans une playlist du client. Possibilité de sauvegarder les éléments suivants:
      - toute la musique qui a été jouée durant l'événement
      - toute la musique qui a été jouée depuis que le client s'est connecté pour la première fois à l'événement
      - des chansons indépendantes
  - Contraintes: Un client ne peut pas enregistrer deux fois la même chanson durant le même événement


- Fonction: Nettoyage de la base de données
    - Objectif: Libérer de la place sur le serveur
    - Description: Permet de supprimer la musique qui correspond aux critères suivants, à choix :
      - n'existe plus sur le disque
      - n'a pas été lue durant l'événement
      - n'a pas été lue depuis une certaine date
    - Contraintes: Nettoyage automatique si la capacité de stockage est limitée


### Côté client
- Fonction: Voir la liste des serveurs accessibles
  - Objectif: Permet de choisir sur quel serveur se connecter
  - Description: Lorsque l'application est lancée, le client voit les serveurs accessibles par leur nom et peut s'y connecter
  - Contraintes: -


- Fonction: Accéder au serveur
  - Objectif: Accéder aux fonctionnalités du serveur
  - Description: Voir la liste de lecture, voter pour changer de chanson ou réorganiser la queue de lecture
  - Contraintes: Les fonctionnalités sont limitées selon la configuration du serveur


- Fonction: Ajouter de la musique au serveur
  - Objectif: Permet au client d'ajouter de la musique sur le serveur pour la lecture
  - Description: Un client peut ajouter sa musique locale à la queue de lecture du serveur
  - Contraintes:
    - Le serveur peut refuser l'ajout de la musique si la configuration de ce dernier n'autorise plus l'ajout de nouvelles chansons
    - Le client ne supporte que les fichiers avec des extensions .mp3 et .m4a


- Fonction: Interface utilisateur
  - Objectif: Interface simplifée pour utiliser le logiciel
  - Description: Voir le mockup en annexe
    - Voir les serveurs accessibles
    - Pouvoir se connecter sur un serveur
    - Voir la queue de lecture du serveur
  - Contraintes: La fenêtre de peut pas être redimensionnée


- Fonction: Système de vote
  - Objectif: Changer de musique, agencer la queue de lecture
  - Description: Donne la possibilité aux utilisateurs de changer ou arranger la musique en fonction des goûts
  - Contraintes: Un client qui vote deux fois pour la même action voit sa deuxième action refusée


- Fonction: Système de favoris/playlist
  - Objectif: Sauvegarder les chansons pour les retrouver après l'événement
  - Description: Sauve la queue de lecture dans la base de données locale - identique à la base de données du serveur, sans le chemin d'accès du fichier - du client selon qu'il souhaite récupérer toute la musique jouée pendant la soirée uniquement dès qu'il s'est connecté pour la première fois ou qu'il souhaite récupérer des chansons indépendantes avec possibilité de créer des playlists
  - Contraintes:
    - Un client ne peut pas enregistrer deux fois la même chanson durant le même événement
    - Un client doit pouvoir supprimer une chanson de ses favoris ou ses playlists
    - Un client doit pouvoir supprimer une playlist avec toutes les chansons contenues dans ladite playlist

## Fonctionnalités optionnelles
Les fonctionnalités listées ci-dessous ne sont pas nécessaires au bon fonctionnement de l'application mais pourront être réalisées si le temps le permet. Ces dernières ne sont pas dans un ordre précis.

### Commun aux deux parties de l'application
- Fonction: Support d'autres formats de musique
  - Objectif: Etendre les possibilités de lecture du serveur
  - Description: FLAC, ALAC, etc.
  - Contraintes: -


- Fonction: Taille de fenêtre non-fixe
  - Objectif: Permet de pouvoir utiliser l'application sur n'importe quelle écran avec n'importe quelle résolution
  - Description: -
  - Contraintes: Taille minimum requise


- Fonction: Fusionner le code de l'application serveur et client
  - Objectif: Permet à n'importe quel client de devenir serveur et inversément
  - Description: -
  - Contraintes: Les deux interfaces graphiques se voudront très similaires, sans possibilité de modification des paramètres du serveur de la part des clients


- Fonction: Filtres de recherche
  - Objectif: Rechercher des chansons sur le serveur (queue de lecture et playlist)
  - Description: Rechercher et mettre dans les favoris ou voter pour une chanson en particulier
  - Contraintes: Recherche limitée aux informations contenues dans la base de données


- Fonction: Intégration de services externes
  - Objectif: Permettre la lecture de chansons issues de services externes (SoundCloud, YouTube, etc.)
  - Description: -
  - Contraintes: La sauvegarde de la session de l'utilisateur est encore à définir


- Fonction: Système de transition dynamique entre chansons
  - Objectif: Transition fluide entre les chansons et les genres
  - Description: Système de transition dynamique entre chansons selon le rythme ou le genre de la musique
  - Contraintes: -


- Fonction: Ajout d'une dimension communautaire
  - Objectif: Interaction entre les utilisateurs
  - Description:
    - Ajout de comptes utilisateurs
    - Partage des chansons et playlists
    - Un compte utilisateur possède une notion de karma et de "rewards" associé au karma
      - Un utilisateur voit son karma augmenter pour une bonne action (voter positivement pour une chanson, mettre sur le serveur de la musique)
      - Un utilisateur voit son karma diminuer pour une mauvase action (voter négativement pour une chanson)
      - Selon le karma, l'utilisateur peut recevoir des avantages
  - Contraintes: Base de données accessible depuis n'importe où pour tous les utilisateurs


- Fonction: Définir des utilisateurs du système comme administrateurs
  - Objectif: Autoriser certains utilisateurs à avoir plus de droits que les autres
  - Description: Leur permettre de mettre la musique sur pause et régler
  - Contraintes: -


### Côté serveur
- Fonction: Configuration avancée du serveur
  - Objectif: Options poussées pour la configuration du serveur
  - Description:
    - Lecture séquentielle: les chansons sont lues les unes après les autres, en ne tenant pas compte des votes : premier arrivé, premier servi
    - Lecture démocratique: les chansons sont lues en fonction des préférences des utilisateurs grâce au système de vote
    - Lecture aléatoire: les chansons sont lues aléatoirement quels que soient les votes
    - Lecture hybride: alternation entre les chansons populaires, qui ont beaucoup de votes, et moins populaires, qui ont moins ou pas de votes
    - Chemin de stockage de la musique: où est enregistrée la musique
  - Contraintes: Refuser les actions effectuées par les clients si elles ne respectent pas la configuration du serveur


## Résumé du fonctionnement du programme
0. Un serveur est lancé et est configuré selon les préférences de la personne qui gère le serveur
0. Le serveur est démarré et les clients peuvent s'y connecter
0. Le client est lancé et voit la liste des serveurs disponibles
0. Le client se connecte sur un serveur
0. Une fois connecté, il peut effectuer les fonctionnalités paramétrées sur le serveur:
  - Proposer de nouvelles chansons
  - Voter pour changer ou organiser la playlist
  - Enregistrer en favoris des chansons ou la liste de lecture
0. Le serveur enregistre la chanson en local et la lit au fur et à mesure de l'événement, en fonction des éventuelles préférences des utilisateurs
0. Une fois l'événement terminé, la musique est conservée sur le serveur jusqu'à ce que l'administrateur décide de nettoyer la base de données ou que la capacité maximum de stockage soit atteinte
0. Le client conserve une copie des metadatas des chansons qui lui ont plu dans sa base de données locale et peut, de ce fait, retrouver les morcaux qui lui ont plu lors de cet événement

## Spécifications techniques
L'application sera réalisée à l'aide des technologies suivantes:
- Java (java.com): pour la réalisation du programme
- JavaFX (docs.oracle.com/javafx): pour la réalisation de l'interface graphique
- SQLite (sqlite.org): pour la réalisation de la base de données
- JSON (json.org): pour l'interaction entre le client et le serveur
- \+ différentes librairies qui pourraient être découvertes durant la conception du programme

Et s'appuiera sur les outils suivants pour sa réalisation:
- Git (git-scm.com) / GitHub (github.com): pour la gestion de versions du projet
- Travis (travis-ci.org): pour les tests unitaires afin de s'assurer du bon fonctionnement de l'application
- PlantUML (plantuml.com): pour la génération des différents schémas (diagrammes de classes, diagrammes de séquences, diagrammes pour le schéma relationnel, etc.)
- Pencil (pencil.evolus.vn): pour la création de mockups et interfaces simplifiées
- \+ différents outils qui pourraient être découverts durant la conception du programme

## Ressources à disposition et organisation
Le projet se déroulera sur tout le semestre pour un total de 90 heures de travail par personne, soit 540 heures de travail effectif sur 14 semaines. Cela représente environ six heures de travail par personne par semaine.
Une métodologie AGILE sera appliquée afin d'avoir un suivi de l'évolution du travail.

## Rendu
En plus des points évoqués dans les contraintes du cours PRO et selon les fonctionnalités importantes, le rendu sera de la forme suivante:
- Un fichier .jar qui représentera le programme côté serveur
- Un fichier de configuration du serveur
- Un fichier .jar qui représente le programme côté client

## Indicateurs et évaluation des résultats
Les différentes itérations de la méthodologie AGILE permettront de quantifier l'avancement du travail et sa bonne réalisation.

## Risques
- envoi de fichiers
- interface
- lecture de fichiers


## Annexes
- Planification
- Mockups de l'application
- Schéma préliminaire de la base de données
- Schéma préliminaire du schéma d'activité
