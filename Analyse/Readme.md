# 🛒 E-commerce Fraud Detection  
Modèle de détection de fraude appliqué à un dataset d’e-commerce provenant de Kaggle.  
L’objectif est d’identifier les transactions frauduleuses grâce à un pipeline complet de Machine Learning incluant prétraitement, gestion du déséquilibre et modélisation.

---

## 📌 1. Description du projet

Les plateformes d’e-commerce subissent de nombreuses tentatives de fraude.  
Ce projet vise à :

- analyser un dataset réel de transactions,
- préparer et nettoyer les données,
- gérer le fort déséquilibre des classes,
- entraîner un modèle prédictif (Logistic Regression),
- évaluer ses performances.

Ce travail permet de comprendre les facteurs influençant la fraude et de construire un modèle operationnel pour les systèmes anti-fraude.

---

## 📦 2. Dataset utilisé

Source :  
👉 https://www.kaggle.com/datasets/umuttuygurr/e-commerce-fraud-detection-dataset

Le dataset contient des informations telles que :

- âge du compte (`account_age_days`)
- distance d’expédition (`shipping_distance_km`)
- fréquence d’achat du client (`total_transactions_user`)
- montant moyen (`avg_transaction_value`)
- type d’appareil utilisé (`device_os`)
- horodatage transformé en sin/cos
- cible : **is_fraud**

Aucune valeur manquante n'était présente.

---

## ⚙️ 3. Pipeline Machine Learning utilisé

```python
# Chargement du dataset
df = pd.read_csv('transactions.csv')

# Séparation X / y
X = df.drop('is_fraud', axis=1)
y = df['is_fraud']

# Standardisation
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# SMOTE pour équilibrer les classes
smote = SMOTE(random_state=42)
X_resampled, y_resampled = smote.fit_resample(X_scaled, y)

# Split train-test
X_train, X_test, y_train, y_test = train_test_split(
    X_resampled, y_resampled, test_size=0.2, random_state=42
)

# Modélisation
model = LogisticRegression(
    class_weight='balanced',
    max_iter=1000,
    random_state=42
)
model.fit(X_train, y_train)

# Prédiction
y_pred = model.predict(X_test)

# Évaluation
print(classification_report(y_test, y_pred))
print(confusion_matrix(y_test, y_pred))
```
## 📊 4. Résultats obtenus

Les métriques calculées incluaient :

- **Accuracy**
- **Precision**
- **Recall**
- **F1-score**
- **Confusion Matrix**

Étant donné l’importance de détecter les fraudes, la métrique clé est :

### 🎯 Recall de la classe 1 (fraude)
Le modèle obtient un **recall élevé**, ce qui signifie qu’il identifie la majorité des fraudes dans les données.  
Bien que cela engendre plus de faux positifs, ce compromis est acceptable dans un système anti-fraude.

### 🔍 Interprétation globale

- Le modèle détecte efficacement les transactions frauduleuses.  
- L’utilisation de **SMOTE** combinée à `class_weight='balanced'` a amélioré la reconnaissance de la classe minoritaire.  
- Le F1-score est stable et montre que le modèle équilibre correctement précision et rappel.

---

## 🧠 5. Conclusion générale

L’analyse montre qu’un pipeline bien structuré (standardisation + SMOTE + Logistic Regression) permet :

- d’équilibrer correctement les classes,
- d’améliorer fortement la détection des fraudes,
- d’obtenir un modèle performant et interprétable,
- de comprendre les variables influençant le comportement frauduleux.

### 🔮 Améliorations possibles

- Tester des modèles plus complexes (Random Forest, XGBoost, LightGBM)  
- Utiliser une recherche d’hyperparamètres (GridSearch / Optuna)  
- Ajouter une explicabilité avancée (SHAP, LIME)  
- Tester des seuils de décision optimisés (ROC / PR curves)
- ## ✨ 7. Auteur

Projet réalisé par **Mohammed Akhoussas**.
