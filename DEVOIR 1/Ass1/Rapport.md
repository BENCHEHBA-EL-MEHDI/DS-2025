## 📊 DESCRIPTION DU DATASET POKER HAND

### **Contexte Général**
Ce dataset provient du UCI Machine Learning Repository et constitue un problème de **classification multi-classe** pour la reconnaissance automatique de mains de poker.

---

### **Structure des Données**

#### **Attributs Prédictifs (10 au total)**
Chaque enregistrement représente une main de **5 cartes** tirées d'un jeu standard de **52 cartes**. Chaque carte est décrite par :

1. **Suit (Couleur)** - 4 valeurs possibles :
   - 1 = Hearts (Cœurs) ♥
   - 2 = Spades (Piques) ♠
   - 3 = Diamonds (Carreaux) ♦
   - 4 = Clubs (Trèfles) ♣

2. **Rank (Rang)** - 13 valeurs possibles :
   - 1 = As, 2-10 = Valeurs numériques, 11 = Valet, 12 = Dame, 13 = Roi

**Format des 10 attributs :**
- S1, R1 (Suit et Rank de la carte 1)
- S2, R2 (Suit et Rank de la carte 2)
- S3, R3 (Suit et Rank de la carte 3)
- S4, R4 (Suit et Rank de la carte 4)
- S5, R5 (Suit et Rank de la carte 5)

---

### **Variable Cible (Classe)**

**11 catégories de mains de poker** (de la plus faible à la plus forte) :

| Classe | Nom | Probabilité | Nombre de combinaisons |
|--------|-----|-------------|------------------------|
| 0 | Nothing (Carte haute) | ~50.12% | 1,302,540 |
| 1 | One Pair (Paire) | ~42.26% | 1,098,240 |
| 2 | Two Pairs (Double paire) | ~4.75% | 123,552 |
| 3 | Three of a Kind (Brelan) | ~2.11% | 54,912 |
| 4 | Straight (Suite) | ~0.39% | 10,200 |
| 5 | Flush (Couleur) | ~0.20% | 5,108 |
| 6 | Full House (Full) | ~0.14% | 3,744 |
| 7 | Four of a Kind (Carré) | ~0.024% | 624 |
| 8 | Straight Flush (Quinte flush) | ~0.0014% | 36 |
| 9 | Royal Flush (Quinte flush royale) | ~0.00015% | **4 ou 480** |

---

### **🔑 PARTICULARITÉ CRUCIALE : L'ORDRE DES CARTES**

#### **Pourquoi 480 Royal Flush au lieu de 4 ?**

**Sans ordre (combinaisons) :**
- 4 Royal Flush possibles (un par couleur : ♥♠♦♣)
- Exemple : {As♥, Roi♥, Dame♥, Valet♥, 10♥}

**Avec ordre (permutations) :**
- Chaque Royal Flush de 5 cartes peut être arrangé de **5! = 120 façons**
- 4 couleurs × 120 permutations = **480 mains distinctes**
- Exemple : (As♥, Roi♥, Dame♥, Valet♥, 10♥) ≠ (Roi♥, As♥, Dame♥, Valet♥, 10♥)

**Implication :** Le dataset considère les **permutations ordonnées**, pas les **combinaisons**, ce qui augmente considérablement le nombre total d'instances possibles :
- **2,598,960 combinaisons** (jeu de poker classique)
- **311,875,200 permutations** (52!/(52-5)! = 52×51×50×49×48)

---

### **Caractéristiques Techniques**

- **Type de problème :** Classification supervisée multi-classe
- **Déséquilibre des classes :** Très important (classes rares vs fréquentes)
- **Nombre d'instances :** Variable selon la version (25,010 à 1,025,010)
- **Valeurs manquantes :** Aucune
- **Type d'attributs :** Entiers catégoriels
- **Applications :** Reconnaissance de patterns, apprentissage sur données déséquilibrées, systèmes de jeu

---

### **Référence**
📁 Source complète : `ftp://ftp.ics.uci.edu/pub/machine-learning-databases/poker/poker-hand.names`
