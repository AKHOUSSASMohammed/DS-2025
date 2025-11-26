# 🏷️ Analyse Machine Learning du Dataset *Wine Quality*
### *Compte rendu complet avec pipeline Python*

---

## 📌 1. Contexte et objectif

L’objectif de ce travail est d’analyser le dataset **Wine Quality** de l’UCI Machine Learning Repository afin de :

- comprendre les relations entre les variables physico-chimiques des vins portugais,  
- explorer la distribution de la qualité du vin,  
- construire un modèle de Machine Learning capable de prédire cette qualité.

Le dataset contient des mesures pour des vins **rouges** et **blancs**, ainsi que leur note sensorielle.

---

## 📊 2. Chargement et exploration de la base de données

Actions réalisées :

- Importation sous forme de DataFrame `pandas`
- Vérification des dimensions et types des colonnes
- Recherche de valeurs manquantes (aucune détectée)
- Visualisation des 5 premières lignes
- Étude de la variable cible `quality`

### 🔎 Observations principales

- **4 898 lignes**
- **11 variables physico-chimiques**
- **Aucune valeur manquante**
- **Distribution déséquilibrée** des classes de qualité

---

## 🔍 3. Prétraitement et visualisation

### ✔️ Analyse de corrélation
- Construction d’une matrice de corrélation
- Heatmap pour visualiser les relations entre variables
- Identification des variables les plus corrélées avec la qualité (ex : taux d’alcool)

### ✔️ Préparation des données
- Séparation en **X** (features) et **y** (quality)
- Split **train / test** avec stratification
- Normalisation via `StandardScaler`

---

## 🤖 4. Pipeline Machine Learning utilisé

### 📦 Code Python du pipeline

```python
# Importation des bibliothèques
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsClassifier
from sklearn.pipeline import Pipeline
from sklearn.metrics import accuracy_score

# Chargement du dataset
df = pd.read_csv("winequality-white.csv", sep=";")

# Variables explicatives et cible
X = df.drop("quality", axis=1)
y = df["quality"]

# Découpage en train/test avec stratification
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)

# Construction du pipeline
pipeline = Pipeline([
    ("scaler", StandardScaler()),                 # Normalisation
    ("knn", KNeighborsClassifier(n_neighbors=5))  # Modèle KNN
])

# Entraînement du modèle
pipeline.fit(X_train, y_train)

# Prédictions
y_pred = pipeline.predict(X_test)

# Évaluation
acc = accuracy_score(y_test, y_pred)
print("Accuracy :", acc)
```
## 📉 5. Résultats obtenus

Les résultats du modèle KNN appliqué au dataset *Wine Quality* montrent que :

- L’accuracy obtenue se situe généralement entre **0.60 et 0.65**, selon la valeur du paramètre *k*.  
- La normalisation via **StandardScaler** améliore significativement les performances du modèle.  
- La répartition déséquilibrée des classes affecte la précision globale, notamment pour les notes les moins représentées.  
- Les faibles valeurs de *k* rendent le modèle plus sensible au bruit, tandis que les valeurs plus élevées stabilisent les prédictions.  
- Les variables les plus influentes identifiées durant l’analyse exploratoire incluent :  
  - le **taux d’alcool**,  
  - l’**acidité volatile**,  
  - la **densité**.

### 💡 Interprétation

Les performances sont correctes pour un modèle simple comme KNN, mais la qualité réelle des prédictions reste limitée par :

- le **déséquilibre du dataset**,  
- la **nature multi-classes** de la variable cible,  
- la **forte proximité** entre certaines classes de qualité (notes 5, 6, 7).

---

## 📝 6. Conclusion générale

Cette étude sur le dataset *Wine Quality* a permis de :

- Explorer la structure et les caractéristiques physico-chimiques des vins portugais.  
- Mettre en place un pipeline complet incluant :  
  - la normalisation des données,  
  - le découpage stratifié du dataset,  
  - l’entraînement d’un modèle KNN.  
- Évaluer les performances du modèle et comprendre ses limites.

Les résultats montrent que **KNN parvient à fournir une précision correcte**, mais qu’il reste limité par :

- la sensibilité à l’échelle des données,  
- le déséquilibre des classes,  
- la complexité de la tâche de classification multi-classes.

### 🔮 Perspectives d’amélioration

Pour aller plus loin, plusieurs pistes peuvent être envisagées :

- tester des modèles plus robustes (**Random Forest**, **SVM**, **Gradient Boosting**) ;  
- appliquer des techniques de rééquilibrage des classes (**SMOTE**, oversampling, class weights) ;  
- optimiser davantage les hyperparamètres ;  
- approfondir l’analyse des relations entre variables via des méthodes avancées.

---
