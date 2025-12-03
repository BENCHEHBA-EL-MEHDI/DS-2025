# 🛒 Analyse de Données E-commerce & Modélisation Prédictive

Ce projet présente une analyse approfondie d'un jeu de données de vente en ligne (produits électroniques). L'objectif est de comprendre les tendances de consommation, la distribution des prix, les corrélations entre variables et d'appliquer un modèle de classification supervisée pour segmenter les produits.

---

## 📊 1. Analyse Exploratoire des Données (EDA)

Cette phase vise à comprendre la structure des données à travers des visualisations descriptives générées via `Seaborn` et `Matplotlib`.

### A. Popularité des Catégories
*Basé sur le graphique : "Top 20 catégories les plus populaires"*

*   **Observation :** Le marché est dominé par les accessoires électroniques.
*   **Analyse :** Les **Câbles USB** et les **Écouteurs (Headphones)** cumulent le plus grand nombre d'avis. Cela suggère des produits à fort volume de vente et à renouvellement fréquent ("Fast Moving Consumer Goods" de l'électronique), contrairement aux appareils plus coûteux comme les télévisions qui apparaissent plus bas dans le classement.

### B. Relation Prix vs Satisfaction Client
*Basé sur le graphique : "Relation entre le prix réel et la note"*

*   **Observation :** Le nuage de points croise le prix avec la note (Rating sur 5).
*   **Analyse :**
    *   **Absence de linéarité :** Il n'y a pas de corrélation évidente entre payer plus cher et être plus satisfait.
    *   **Concentration :** La majorité des produits se situent dans l'entrée de gamme (< 20 000 ₹) avec des notes très variées.
    *   **Stabilité du Haut de Gamme :** Les produits chers (> 60 000 ₹) ont moins de variance dans les notes, se situant souvent au-dessus de 4/5.

### C. Distribution des Prix
*Basé sur le graphique : "Distribution des prix remisés"*

*   **Observation :** L'histogramme montre une distribution fortement **asymétrique vers la droite** (right-skewed).
*   **Analyse :** L'immense majorité du catalogue est constituée de produits à bas prix. La longue traîne vers la droite indique que les produits "Premium" ou très chers sont des valeurs aberrantes (outliers) en termes de fréquence.

---

## 🔗 2. Analyse des Corrélations

Pour sélectionner les meilleures *features* pour nos modèles, nous avons étudié la matrice de corrélation (Heatmap).

*   **Multicolinéarité identifiée :** `discounted_price` et `actual_price` ont une corrélation de **0.96**. Un produit cher à la base reste cher après remise.
*   **Indépendance de la note :** Le `rating` est très peu corrélé au prix (`0.12`), confirmant l'analyse visuelle précédente.
*   **Variable Cible :** La variable `target_binary` montre une corrélation significative (**~0.40**) avec les prix, suggérant que le prix est un bon discriminateur pour la classification binaire (ex: segmentation Haut de gamme vs Bas de gamme).

---

## 🤖 3. Modélisation : Régression Logistique

Nous avons entraîné un modèle de régression logistique pour effectuer une classification binaire sur des données synthétiques basées sur les caractéristiques du dataset.

### 📈 Performance du Modèle
*   **Accuracy (Précision) :** `98.67%`
*   Le modèle est extrêmement performant pour séparer les deux classes.

### 📐 La Frontière de Décision
Le graphique de régression logistique visualise la **droite de décision** (ligne noire) qui sépare l'espace vectoriel :

*   **Zone Rouge :** Probabilité > 50% pour la Classe 1.
*   **Zone Bleue :** Probabilité > 50% pour la Classe 0.

L'équation de la droite séparatrice obtenue est :

$$ 0.629 \cdot X + 3.538 \cdot Y - 0.697 = 0 $$

**Interprétation des coefficients :**
Le coefficient associé à la variable Y (**3.538**) est nettement supérieur à celui de X (**0.629**). Cela signifie que la caractéristique en ordonnée (Feature_Y) a un poids beaucoup plus important dans la décision du modèle que la caractéristique en abscisse.

---

## 📝 Conclusion

Ce projet démontre que :
1.  **Le Prix ne fait pas le bonheur :** Dans ce marché, un prix élevé ne garantit pas une meilleure note client.
2.  **Volume vs Valeur :** Le marché est tiré par des accessoires à faible coût mais à fort volume.
3.  **Efficacité de la Régression Logistique :** Lorsque les variables sont linéairement séparables (comme démontré dans la partie modélisation), un modèle simple comme la régression logistique offre une précision quasi-parfaite (**>98%**) tout en restant facilement interprétable grâce à ses coefficients.
