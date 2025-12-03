# Descriptif du Projet – Prédiction de la Densité du Trafic Urbain

Ce projet utilise le dataset *Urban Traffic Density in Cities* afin de construire un modèle de **régression** capable d’estimer la densité du trafic urbain à partir de diverses caractéristiques collectées dans un environnement urbain.

## Contenu de l'analyse

### 1. Pré-traitement des données
Le dataset a été nettoyé et préparé pour l’analyse :
- suppression des doublons,
- imputation des valeurs manquantes,
- encodage des variables catégorielles (One-Hot),
- standardisation des variables numériques.

### 2. Analyse exploratoire (EDA)
Une exploration visuelle et statistique a permis d’observer :
- la distribution des variables (histogrammes, boxplots),
- les relations et corrélations (heatmap),
- les variables les plus influentes sur la densité du trafic.

### 3. Modélisation
Plusieurs modèles de régression ont été testés afin d’identifier celui offrant les meilleures performances :
- Linear Regression,
- Random Forest Regressor,
- Gradient Boosting Regressor.

Les performances ont été évaluées via les métriques suivantes :
- **RMSE** (Root Mean Squared Error),
- **MAE** (Mean Absolute Error),
- **R²** (coefficient de détermination).

### 4. Objectif
L’objectif général est de développer un modèle capable de prédire efficacement la densité du trafic et d’analyser les facteurs qui contribuent le plus à cette variation.

