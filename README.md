## Application communautaire de streaming de musique

### Introduction

La musique a une part importante dans toute manifestation \(anniversaire, concert, bar, soirée entre amis, etc.\). Néanmoins, la musique est souvent gérée par une personne sur un appareil. Nous souhaitons proposer une application de type client-serveur qui permet aux différents utilisateurs de proposer leur propre musique au serveur, qui les jouera au fur et à mesure de l'événement.

### Fonctionnalités importantes

* Transférer et jouer de la musique sur le serveur
* Effectuer les actions de base sur la musique \(jouer, arrêter, supprimer, changer de chanson, voir la queue de lecture\)
* Système de vote pour changer la musique
* Sauvegarder les titres envoyés au serveur pour une \(re\)lecture des morceaux
* Sauvegarder un titre ou la queue de lecture \(sur le serveur\)
* Création de profils utilisateur permettant de sauvegarder un titre ou la queue de lecture

### Fonctionnalités optionnelles

* Choix d'être le serveur ou le client
* Filtres de recherche
* Possibilité de pouvoir se connecter à différents serveurs de streaming
* Intégration de services externes \(SoundCloud, Spotify, etc.\)
* Système de transition dynamique entre chansons selon le rythme ou le genre de la musique

### Thématiques abordées

* Architecture client-serveur
* Envoi et lecture de fichiers sur un serveur
* Gestion/archivage de fichiers
* Gestion de profils utilisateur
* Intégration/ajout de services externes
* Algorithmes de détection du genre musical

## Application de communication professeurs-élèves

### Introduction

Tout au long de nos études, nous avons eu le plaisir de rencontrer plusieurs professeurs mais un problème revenait souvent : la normalisation des documents et/ou des rendus. Pour contrer ce genre de problème, nous avons eu pour idée de créer une application client-serveur permettant de faciliter la vie aux deux partis.

### Fonctionnalités importantes

* Créer et gérer des classes de personnes \(étudiants et professeurs\)
* Possibilité de créer des leçons/échéances pour toute la classe \(date de tests, d'examens, de rendu de laboratoires, etc.\)
* Liste d'absence pour les professeurs : le professeur accorde trois minutes aux étudiants pour signaler qu'ils sont présents. Passé ce délai, le reste est noté absent.
* Centraliser les documents de chaque cours \(cas typiques : 1/4 des .pdf sur Cyberlearn, une moitié sur eistore et le reste dans la nature\)

### Fonctionnalités optionnelles

* Système de questionnaire \(QCM, Quizz\) avec visualisation des statistiques.
* Système de feedback facultatif et rapide sur le cours proposé de façon régulière, tout au long du semestre
* Signature des rendus afin d'être sûr de l'identité de l'expéditeur.
* Intégration avec GAPS ? Permettrait l'implémentation de beaucoup d'autres fonctionnalités plus ou moins importantes \(consultation des notes, de l'agenda, système de cache pour moins d'attente, etc.\)

### Thématiques abordées

* Architecture client-serveur
* Gestion d'utilisateurs et de leurs droits
* Gestion de fichiers par la centralisation
* Questionnaires interactifs et création de statistiques
* Technologies de signature des documents



