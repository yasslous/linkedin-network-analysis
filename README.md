🚀 LinkedIn Link Prediction & Community Analysis 

📌 Description Générale

Ce projet explore la structure des réseaux professionnels à partir de données extraites de LinkedIn. L'objectif est double : d'une part, cartographier les communautés d'employés partageant des caractéristiques communes, et d'autre part, prédire les opportunités de carrière (Link Prediction) en identifiant quelles entreprises correspondent le mieux au profil d'un employé donné.

📊 Les Données
Le jeu de données se compose de profils LinkedIn incluant :

Identité : Nom de l'employé.

Emploi actuel : Entreprise, industrie.

Localisation : Ville et code pays.

Formation : Détails sur l'éducation.

❓ Problématique
Comment transformer un réseau professionnel brut en un outil de recommandation stratégique ?
Nous cherchons à répondre à deux questions :

Peut-on identifier des groupes d'influence (communautés) sans connaître les liens hiérarchiques ?

Est-il possible de prédire avec précision si un employé est susceptible de rejoindre une entreprise spécifique en se basant sur sa position dans le réseau et ses attributs ?

💡 Solution
Nous avons mis en place une approche hybride :

Analyse de Graphes : Modélisation d'un graphe biparti (Employé-Entreprise) et projection d'un graphe de similarité entre employés.

Détection de Communautés : Application de l'algorithme de Louvain pour segmenter le réseau.

Machine Learning : Utilisation de la Régression Logistique pour prédire la probabilité de liens futurs, en utilisant des features topologiques et attributaires.

📂 Organisation du Projet
Le projet est découpé en notebooks progressifs pour une lecture fluide :

01_nettoyage_donnees.ipynb : Préparation et nettoyage des données LinkedIn (gestion des doublons, formatage).

02_graphe_biparti.ipynb : Construction du graphe biparti Employés ↔ Entreprises et analyse des premières statistiques du réseau.

03_projection_vers_employee.ipynb : Calcul d'un score de similarité robuste entre employés (Ville, Industrie, Éducation) et création de la matrice d'adjacence, en ignorant les valeurs manquantes pour éviter les biais.

04_detection_communautes.ipynb : Mise en œuvre de l'algorithme de Louvain. Obtention d'une modularité de 0.93 et répartition des employés en clusters cohérents.

05_preparation_pour_prediction.ipynb : Création du dataset pour le Machine Learning. Génération d'échantillons négatifs et extraction de features (degrés, attachement préférentiel, appartenance aux clusters).

06_prediction_lien.ipynb : Comparaison des modèles (Random Forest vs Régression Logistique). Utilisation du modèle le plus performant pour générer des recommandations de carrière concrètes.

📈 Résultats Clés
Modularité Moyenne : Une structure communautaire moyenne (0.21), mais il a résussi à segmenter le réseau en nombre réduit de clusters.

Performance ML : La Régression Logistique s'est révélée être le modèle le plus robuste pour capturer les relations linéaires entre les attributs des employés et leur entreprise cible.

Système de Recommandation : Génération d'un fichier de probabilités permettant d'identifier les futurs recrutements les plus probables.

🛠️ Installation & Utilisation
Clonez le dépôt : git clone ...

Installez les dépendances : pip install pandas networkx scikit-learn matplotlib seaborn

Exécutez les notebooks dans l'ordre de 01 à 06.
