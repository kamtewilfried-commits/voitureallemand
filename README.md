# AutoDrive

Application Android native en Kotlin pour la location de voitures. Un utilisateur consulte le catalogue, filtre les voitures, réserve un véhicule, suit ses réservations, gère son profil et laisse des évaluations. Un espace administrateur permet de gérer les voitures disponibles.

Projet réalisé en équipe de trois au Cégep Rosemont (Technique informatique).

## Fonctionnalités

- Connexion d'un utilisateur avec sauvegarde de la session
- Liste des voitures avec recherche et filtrage par marque, modèle, année, prix et disponibilité
- Fiche détaillée d'une voiture : images, description et évaluations
- Réservation avec calcul du coût total et détection des conflits de réservation
- Historique des réservations et annulation des réservations actives
- Profil utilisateur et préférences locales
- Ajout et modification d'évaluations
- Espace administrateur : ajout, modification et suppression de voitures

## Architecture MVP

Le projet suit une architecture MVP :

- **Model** : entités Room, DAO et repositories (`app/src/main/java/com/example/autodrive/model`)
- **View** : Activities et écrans Compose, qui affichent les données et transmettent les actions de l'utilisateur
- **Presenter** : classes qui font le lien entre la vue et le modèle (`app/src/main/java/com/example/autodrive/presenter`)
- **Contracts** : interfaces entre les vues et les presenters (`presenter/contract`)

Les presenters couvrent les voitures, le catalogue client, les réservations et l'historique des réservations.

## Base de données (SQLite / Room)

La persistance repose sur Room, au-dessus de SQLite. La base est déclarée dans `AppDatabase.kt`.

| Table | Contenu |
| --- | --- |
| `voiture` | Voitures disponibles à la location |
| `utilisateur` | Utilisateurs de l'application |
| `reservation` | Réservations, reliées aux voitures |
| `evaluation` | Avis et notes sur les voitures |

## Installation

Prérequis : Android Studio récent, JDK compatible avec Gradle Android, SDK Android installé.

1. Cloner le dépôt.
2. Ouvrir le dossier dans Android Studio.
3. Laisser Gradle synchroniser les dépendances.

## Exécution

Depuis Android Studio : choisir un émulateur ou un appareil, puis lancer la configuration `app`.

Depuis un terminal :

    .\gradlew.bat assembleDebug

Puis installer l'APK de débogage sur un appareil ou un émulateur.

## Tests

Tests unitaires :

    .\gradlew.bat testDebugUnitTest

Tests instrumentés Android :

    .\gradlew.bat connectedDebugAndroidTest

Les tests unitaires portent sur la logique des presenters et des repositories, avec des objets factices pour isoler chaque composant.
