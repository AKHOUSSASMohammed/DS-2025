
<img src="IMG-20250509-WA0029.jpg" style="height:464px;margin-right:432px"/>

# Compte Rendu de la Base de Données "Adult" (Census Income)

## Vue d'ensemble

La base de données **Adult**, également connue sous le nom de "Census Income", est un jeu de données extrait du recensement américain de 1994 par Barry Becker. Elle a été mise à disposition le 30 avril 1996 et est hébergée sur le dépôt UCI Machine Learning Repository.

## Objectif de l'analyse

L'objectif principal est de **prédire si le revenu annuel d'un individu dépasse 50 000 dollars par an** sur la base de données démographiques et socio-économiques issues du recensement.

## Caractéristiques de la base de données

### Dimensions
- **Nombre d'instances** : 48 842 enregistrements
- **Nombre de variables** : 14 variables prédictives + 1 variable cible
- **Type de tâche** : Classification binaire (>50K ou ≤50K)
- **Nature des données** : Multivariée (catégorielle et numérique)

### Qualité des données
- La base contient des **valeurs manquantes** (notamment dans les variables `workclass` et `occupation`)
- Les enregistrements ont été nettoyés selon des critères spécifiques : âge >16 ans, revenu ajusté brut >100, poids final >1, heures de travail par semaine >0

## Description détaillée des variables

### Variables numériques (6)

1. **age** : Âge de l'individu (continu)
2. **fnlwgt** : Poids final (final weight) - représente le nombre de personnes que cet enregistrement représente dans la population
3. **education-num** : Nombre d'années d'éducation (continu)
4. **capital-gain** : Gains en capital (continu)
5. **capital-loss** : Pertes en capital (continu)
6. **hours-per-week** : Heures de travail par semaine (continu)

### Variables catégorielles (8)

1. **workclass** : Type d'employeur
   - Catégories : Private, Self-emp-not-inc, Self-emp-inc, Federal-gov, Local-gov, State-gov, Without-pay, Never-worked
   - Contient des valeurs manquantes

2. **education** : Niveau d'éducation
   - 16 catégories allant de Preschool à Doctorate

3. **marital-status** : Statut matrimonial
   - 7 catégories : Married-civ-spouse, Divorced, Never-married, Separated, Widowed, Married-spouse-absent, Married-AF-spouse

4. **occupation** : Type d'occupation professionnelle
   - 14 catégories incluant Tech-support, Sales, Exec-managerial, Prof-specialty, etc.
   - Contient des valeurs manquantes

5. **relationship** : Relation dans le foyer
   - 6 catégories : Wife, Own-child, Husband, Not-in-family, Other-relative, Unmarried

6. **race** : Origine ethnique
   - 5 catégories : White, Asian-Pac-Islander, Amer-Indian-Eskimo, Other, Black

7. **sex** : Sexe (binaire)
   - Female, Male

8. **native-country** : Pays d'origine
   - Plus de 40 pays représentés, avec une majorité d'États-Unis

### Variable cible

**income** : Revenu annuel en deux classes
- ">50K" : Revenu supérieur à 50 000 dollars
- "≤50K" : Revenu inférieur ou égal à 50 000 dollars

## Fichiers disponibles

- **adult.data** (3,8 MB) : Jeu d'entraînement
- **adult.test** (1,9 MB) : Jeu de test
- **adult.names** : Documentation
- **old.adult.names** : Documentation ancienne

## Pertinence pour l'analyse prédictive

Cette base de données est particulièrement adaptée pour :

- **L'apprentissage supervisé** avec des algorithmes de classification
- **L'analyse de l'équité** dans les modèles de machine learning (présence de variables démographiques sensibles)
- **L'étude des facteurs socio-économiques** influençant le revenu
- **Le benchmarking de modèles** (dataset largement utilisé dans la littérature avec plus de 257 publications le citant)

## Points d'attention

- La présence de valeurs manquantes nécessite une stratégie de traitement appropriée
- Les variables démographiques sensibles (race, sexe) requièrent une attention particulière concernant les biais potentiels
- Le dataset date de 1994, ce qui peut limiter sa représentativité pour des analyses contemporaines
- Le seuil de 50 000 dollars n'a pas été ajusté pour l'inflation

## Licence

Le dataset est sous licence Creative Commons Attribution 4.0 International (CC BY 4.0), permettant son utilisation libre avec attribution appropriée.
