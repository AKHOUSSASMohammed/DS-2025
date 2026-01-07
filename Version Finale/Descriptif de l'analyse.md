# Descriptif du Projet – Analyse et Classification de la Densité du Trafic dans une Ville Futuriste

Ce projet utilise le dataset *Futuristic City Traffic* afin d’analyser le comportement du trafic dans un environnement urbain futuriste et de construire un modèle de classification capable de prédire les niveaux de densité (faible, moyen, élevé) à partir de différentes caractéristiques liées à la mobilité, à la météo et au contexte urbain.

---

## 📌 Contenu de l’analyse

### **1. Pré-traitement des données**

Le dataset a été préparé afin d’assurer une modélisation fiable :

- inspection de la structure et des types de données,  
- traitement des valeurs manquantes si nécessaire,  
- transformation de la densité du trafic en trois classes (faible, moyen, élevé),  
- encodage des variables catégorielles via Label Encoding pour accélérer la modélisation,  
- séparation des données en ensembles d’entraînement et de test.

---

### **2. Analyse exploratoire (EDA)**

Une analyse statistique et graphique a permis de mieux comprendre les caractéristiques du trafic futuriste :

- observation de la distribution des variables,  
- analyse des zones géographiques, conditions météorologiques et types de véhicules,  
- mise en évidence des relations entre les variables et la densité du trafic,  
- étude des facteurs pouvant influencer la congestion dans un contexte urbain avancé.

---

### **3. Modélisation**

Un modèle de classification a été mis en place afin d’identifier les niveaux de densité du trafic :

- transformation de la variable cible en classes par quantiles,  
- encodage rapide des variables catégorielles,  
- entraînement d’un modèle de **Logistic Regression** pour garantir une exécution rapide et stable même avec un grand volume de données.

L’évaluation du modèle a été réalisée à travers :

- la matrice de confusion,  
- les mesures de classification standard (accuracy, precision, recall),  
- la capacité du modèle à distinguer correctement les niveaux de trafic.

---

### **4. 🎯 Objectif**

L’objectif général est de fournir une analyse complète des données de trafic d’une ville futuriste et de construire un modèle capable de prédire efficacement le niveau de densité du trafic. Cette étude permet également d’identifier les variables les plus influentes, offrant une base solide pour le développement futur de systèmes intelligents de gestion du trafic dans des environnements urbains avancés.
