# Compte Rendu Analyse MyAnimeList

## Introduction

Ce projet vise à **explorer** et **analyser** un dataset issu de MyAnimeList, une base de données d’animes, à l’aide de Python (Pandas, Seaborn, Scikit-Learn…). L’accent est mis sur la compréhension des variables, la visualisation des données et la création d’un modèle de prédiction de score.

## Objectifs
- Charger et nettoyer le dataset
- Explorer les différentes variables (Score, Type, Épisodes…)
- Visualiser les distributions et relations
- Modéliser le score avec une régression linéaire
- Évaluer le modèle

## Méthodes

### Traitement des données
- Chargement via pandas (`read_csv`)
- Nettoyage de la colonne `Episodes` : conversion en valeur numérique et gestion des valeurs manquantes.
- Extraction de l’année de première diffusion (`PremieredYear`) à partir de chaînes de caractères.
- Conversion en valeurs numériques des colonnes Popularity, Members, Favorites.
- Préparation de la matrice de features et de la cible pour la modélisation.

### Exploration et visualisations
- **Aperçu du dataset** (head, .shape, colonnes)
- Histogramme de la distribution des scores
- Countplot des types d’anime
- Boxplot pour repérer les valeurs atypiques sur le score
- Cartes de corrélation (heatmap, pairplot) pour explorer les liens entre variables
- Statistiques descriptives sur les colonnes principales

### Modélisation (régression linéaire)
- Features : `Episodesclean` et `PremieredYear`
- Split en train/test (20% test)
- Entraînement d’un modèle de régression linéaire (Scikit-learn)
- Évaluation : Mean Squared Error (MSE) et R²
- Affichage graphique : valeurs réelles vs prédites (scatterplot)

## Résultats

- **Distribution des scores** : majoritairement centrée, quelques outliers
- **Nombre d’animes par type** : forte représentation de certaines catégories (série, film…)
- **Corrélations** : résultats généralement faibles entre features et score
- **Performance du modèle** :
    - Mean Squared Error modéré
    - Un R² très faible, le score des animes s’expliquant peu par `Episodesclean` et `PremieredYear`

## Conclusion

- Le nettoyage et la préparation sont cruciaux pour toute analyse.
- La corrélation faible entre variables expliquant le score implique que d’autres facteurs déterminants sont absents ou non pris en compte.
- L’usage d’autres méthodes (features ou modèles) serait nécessaire pour améliorer la prédiction.
- La visualisation permet d’avoir une vue claire sur la qualité et la structure du dataset.
