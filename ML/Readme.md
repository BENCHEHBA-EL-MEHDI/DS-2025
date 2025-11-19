# Compte Rendu TP - Machine Learning

## Introduction

Ce TP porte sur la **classification supervisée** via la méthode des **k plus proches voisins (k-NN)**. L'objectif est d'apprendre à prédire une catégorie (par exemple, qualité d'un vin ou groupe d'âge santé) à partir de plusieurs variables mesurées.

## Objectifs

- Charger et explorer un dataset réel (santé/nutrition ou qualité du vin).
- Effectuer la préparation des données (séparation features/labels, transformation des cibles...).
- Appliquer un modèle de classification (k-NN).
- Analyser la performance en utilisant différentes valeurs de k et en comparant les courbes d'erreur.
- Discuter l'impact de la normalisation des données.

## Méthodes

### 1. Chargement et exploration

- Utilisation de pandas et numpy pour charger le dataset.
- Observation des premiers échantillons et résumé statistique.
- Examen des distributions des classes (ex : adulte/senior ou bon/mauvais vin).

### 2. Préparation des données

- Création des matrices de features (X) et labels (y).
- Transformation des cibles pour obtenir un problème binaire.
- Séparation aléatoire des données en train/validation/test tout en respectant la proportion de chaque classe.

### 3. Classification k-NN

- Expérimentation du modèle k-NN pour différentes valeurs de k.
- Calcul des taux d’erreur sur train et validation.
- Observation et interprétation de l’overfitting avec courbes d’apprentissage.

### 4. Normalisation

- Application de la normalisation (centrage/réduction) pour rendre les variables comparables.
- Comparaison des résultats obtenus avec données brutes et données normalisées.

## Résultats

- Visualisation des distributions de variables et des corrélations.
- Présentation des courbes d’erreur selon k, avec analyse du sur/apprentissage.
- Détermination du meilleur k en se basant sur l’erreur de validation.
- Comparaison des performances avec et sans normalisation.

## Conclusion

- Le choix de k optimal est essentiel : trop petit → surapprentissage, trop grand → sous-apprentissage.
- La normalisation améliore souvent les performances des modèles sensibles à l’échelle.
- La bonne pratique impose de séparer les ensembles de données de façon stratifiée pour évaluer correctement la généralisation.
- Les performances doivent être interprétées avec précaution, la robustesse se vérifie via la stabilité des résultats sur différents splits/normalisations.

