# Transport et Smart-Cities | Prédiction de la Densité du Trafic Urbain

![Image](https://raw.githubusercontent.com/AKHOUSSASMohammed/DS-2025/4cf334f2a4952eea59150946e5327983ef082b0f/Version%20Finale/IMG-20250509-WA0026.jpg)

> **À propos de moi**  
> Étudiant en cycle de Gestion à l’ENCG, orienté vers le contrôle de gestion et la finance d’entreprise. Intéressé par l’analyse de la performance et la budgétisation, avec des bases en comptabilité, audit et normes IFRS acquises lors d’un stage en cabinet d’expertise comptable.

## 1. Introduction
Le développement des villes intelligentes repose sur la capacité à anticiper la congestion urbaine. La prédiction du trafic permet d’optimiser les déplacements, d’améliorer la qualité de vie et de réduire l’empreinte écologique.

Ce projet s’appuie sur le dataset *Urban Traffic Density in Cities* (Kaggle) afin de construire un modèle de régression capable d’estimer la densité du trafic urbain à partir de caractéristiques temporelles, géographiques et contextuelles.

---

## 2. Méthodologie

### 2.1 Pré-traitement des données
Les étapes suivantes ont été appliquées pour préparer les données :

- suppression des doublons,  
- gestion des valeurs manquantes,  
- encodage des variables catégorielles (One-Hot Encoding),  
- standardisation des variables numériques,  
- séparation en données d’entraînement (80%) et de test (20%).

Ces transformations garantissent un dataset propre et compatible avec les modèles de régression.

---

### 2.2 Analyse exploratoire (EDA)
L’exploration visuelle et statistique a permis de :

- observer la distribution des variables (histogrammes, boxplots),  
- détecter les relations et dépendances (heatmap de corrélation),  
- identifier les variables les plus influentes,  
- ajouter de nouvelles variables issues du *feature engineering* (période de la journée, indicateur week-end).

Ces résultats ont servi à orienter les choix de modèles.

---

## 3. Modélisation

Trois modèles de régression ont été testés :

- **Linear Regression**  
- **Random Forest Regressor**  
- **Gradient Boosting Regressor**

Tous ont été évalués selon trois métriques :  
RMSE, MAE et R².

---

## 4. Résultats

Les performances des modèles sur le jeu de test sont résumées dans le tableau suivant :

| Modèle | RMSE | MAE | R² |
|--------|------|------|-----|
| **Linear Regression** | **0.1284** | — | — |
| **Random Forest Regressor** | — | — | — |
| **Gradient Boosting Regressor** | — | — | — |

Le modèle de régression linéaire fournit un RMSE de **0.1284**, ce qui constitue une première base de comparaison.  
Les modèles d’ensemble (Random Forest et Gradient Boosting) devraient théoriquement mieux capturer la non-linéarité du trafic urbain.

---

## 5. Discussion

L’analyse des résidus montre que les variations soudaines du trafic (heures de pointe, zones très fréquentées) génèrent les erreurs les plus élevées.  
Les variables temporelles se révèlent déterminantes pour la prédiction, confirmant la nature cyclique du trafic urbain.

---

## 6. Conclusion

Ce travail a permis de mettre en place une chaîne complète : nettoyage des données, exploration, features dérivées, modélisation et évaluation.  
Le RMSE obtenu montre que la prédiction est déjà fiable, mais plusieurs pistes d'amélioration restent possibles :

- intégration de données météo,  
- modèles séquentiels (LSTM, Prophet),  
- enrichissement géospatial,  
- optimisation avancée des hyperparamètres.

