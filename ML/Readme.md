# NOM: AKHOUSSAS Mohammed
# Filière: contrôle,audit et conseil
# Groupe:1

# Rapport descriptif : Analyse Machine Learning de la qualité des vins

## Introduction

Ce notebook a pour objectif de modéliser la qualité de vins portugais à partir de différentes variables physico-chimiques. L’analyse s’appuie sur le dataset Wine Quality de l’UCI Machine Learning Repository, contenant des mesures relatives à des vins rouges et blancs. Ce jeu de données sert de base à une exploration descriptive ainsi qu’à la construction de modèles prédictifs de la qualité du vin.

## Bibliothèques utilisées

Les principales bibliothèques mobilisées sont :

 - pandas et numpy pour la manipulation et le traitement des données ;

 - matplotlib et seaborn pour la visualisation graphique ;

 - scikit-learn (sklearn) pour l’implémentation des algorithmes de Machine Learning (séparation train/test, KNeighborsClassifier, métriques de performance, etc.) ;

 - ucimlrepo pour l’importation structurée du jeu de données depuis l’UCI ML Repository.

## Chargement et exploration du jeu de données

Le jeu de données est importé depuis une source en ligne puis converti en DataFrame pandas. Une première exploration présente les dimensions du dataset, les types de variables ainsi que la présence éventuelle de valeurs manquantes. Un aperçu des cinq premières lignes est également affiché.
L’étude préliminaire de la variable cible quality permet d’observer la distribution des notes attribuées aux vins.

 - Principales observations :

 - 4 898 échantillons ;

 - 11 variables physico-chimiques + 1 variable qualitative (qualité) ;

 - aucune valeur manquante détectée ;

 - répartition des classes de qualité déséquilibrée.

## Prétraitement et visualisation

Une analyse des corrélations est réalisée à travers une matrice affichée sous forme de heatmap afin d’identifier les relations entre les variables et la qualité du vin.
Les données sont ensuite divisées entre variables explicatives (X) et variable cible (y), puis séparées en jeux d’entraînement, de validation et de test selon une stratégie de stratification pour préserver la distribution des classes.

## Modélisation : Algorithme K-Nearest Neighbors (KNN)

L’analyse repose sur l’algorithme des k plus proches voisins (KNeighborsClassifier) dans le cadre d’une classification supervisée :

 - optimisation de l’hyperparamètre k (nombre de voisins) à l’aide d’une validation croisée réalisée sur le set de validation ;

 - évaluation des performances du modèle via différentes métriques, notamment l’accuracy et le taux d’erreur pour chaque valeur testée de k ;

 - visualisation graphique de la variation de l’erreur en fonction de k.

### Exemple de pipeline :

```python
# Importation des bibliothèques
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsClassifier
from sklearn.pipeline import Pipeline
from sklearn.metrics import accuracy_score

# Chargement du dataset (exemple avec un fichier CSV local)
df = pd.read_csv("winequality-white.csv", sep=";")

# Variables explicatives et cible
X = df.drop("quality", axis=1)
y = df["quality"]

# Découpage en train/test
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)

# Construction du pipeline
pipeline = Pipeline([
    ("scaler", StandardScaler()),       # Normalisation des données
    ("knn", KNeighborsClassifier(n_neighbors=5))  # Modèle KNN
])

# Entraînement du modèle
pipeline.fit(X_train, y_train)

# Prédictions
y_pred = pipeline.predict(X_test)

# Accuracy
acc = accuracy_score(y_test, y_pred)
print("Accuracy :", acc)

```

## Conclusion

L’analyse menée sur le jeu de données Wine Quality a permis de comprendre l’impact des différentes caractéristiques physico-chimiques sur la qualité des vins portugais. Après une exploration approfondie des données, un prétraitement adapté et l’application d’un pipeline de Machine Learning, le modèle K-Nearest Neighbors s’est révélé pertinent pour cette tâche de classification, à condition d’ajuster correctement son hyperparamètre principal, le nombre de voisins k.

Bien que la répartition déséquilibrée des classes constitue une limite pour la précision globale du modèle, les résultats obtenus démontrent la capacité des approches supervisées à prédire efficacement la qualité du vin à partir de mesures objectives. Cette étude met en évidence l’importance du prétraitement (normalisation, stratification) et de l’évaluation rigoureuse des performances pour obtenir un modèle fiable.

Enfin, l’utilisation d’un pipeline structuré assure une meilleure reproductibilité de l’analyse et offre une base solide pour l’intégration d’autres algorithmes ou techniques d’optimisation dans de futurs travaux.
