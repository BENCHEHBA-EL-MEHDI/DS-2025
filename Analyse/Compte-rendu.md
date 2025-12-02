# Compte Rendu Analyse Dataset Toyota

BENCHEHBA EL MEHDI 24011415

<img src="signal-2025-05-10-050004_002.png" style="height:464px;margin-right:432px"/>


## Introduction

Ce projet analyse un dataset comprenant des informations sur des véhicules Toyota, telles que année, prix, kilométrage, taxe, consommation (mpg), taille moteur, et d’autres caractéristiques. L’objectif est d’explorer ces données, d’en extraire des variables importantes, et de modéliser le prix du véhicule en fonction des autres variables.

## Objectifs

- Charger et nettoyer complètement le dataset.
- Réaliser des analyses statistiques descriptives pour comprendre la distribution des variables.
- Visualiser les relations entre variables par corrélations et graphiques.
- Effectuer une régression linéaire pour prédire le prix selon des variables explicatives.
- Mettre en œuvre une régression logistique pour modéliser la probabilité qu’un véhicule ait un prix élevé.
- Évaluer les résultats des modèles et interpréter les relations.

## Méthodes

### Nettoyage et prétraitement des données

- Suppression des lignes entièrement vides.
- Remplissage des valeurs manquantes :
  - Moyenne pour les colonnes numériques.
  - Modalité la plus fréquente pour les colonnes catégorielles.
- Suppression des doublons pour garantir la qualité des données.
- Normalisation des variables numériques pour homogénéiser les échelles.
- Encodage des variables catégorielles en variables indicatrices (One-Hot Encoding).
- Nettoyage et standardisation des chaînes de caractères (minuscules, suppression des espaces).

### Analyse exploratoire

- Description statistique (moyenne, écart-type, minimum, maximum, quartiles).
- Visualisation par histogrammes, boxplots et heatmap des corrélations.
- Étude détaillée des variables clés : année, prix, kilométrage, taxe, consommation, taille moteur.
- Analyse des relations entre variables par matrice de corrélation.

### Modélisation

- Régression linéaire pour modéliser le prix en fonction de l’année.
- Régression logistique pour modéliser la classification binaire du prix en prix élevé vs prix bas (seuil basé sur la médiane).
- Tracés graphiques des droites de régression et de la courbe sigmoïde, avec les données réelles.

## Résultats

- Le dataset comporte 6738 véhicules avec 9 variables principales.
- La variable prix présente une large variation (de 850 à près de 60 000 unités).
- Des corrélations positives importantes observées entre prix et taille de moteur, ainsi qu’entre prix et année.
- Corrélations négatives entre kilométrage et prix, ainsi qu’entre consommation et prix.
- Le modèle de régression linéaire montre une tendance positive entre année et prix (plus récente → plus cher), bien que la dispersion soit importante.
- Le modèle de régression logistique distingue raisonnablement les véhicules chers des moins chers selon l’année.
- Les graphiques confirment visuellement la capacité des modèles à capturer certaines tendances principales.

## Conclusion

- Un nettoyage rigoureux des données est fondamental pour obtenir des analyses précises et fiables.
- La modélisation linéaire donne une première approximation convaincante mais limitée, invitant à considérer plus de variables explicatives.
- La classification par régression logistique permet d’anticiper le positionnement du véhicule en terme de prix haut/bas, utile pour la prise de décision commerciale.
- Des approfondissements seraient nécessaires pour intégrer davantage de facteurs et améliorer la prédiction, notamment via des modèles non linéaires ou des méthodes d’ensemble.
- Les visualisations aident à mieux comprendre la structure des données et à présenter clairement les résultats.


