# Régression vs Classification en Machine Learning

## 1. Introduction

En Machine Learning, deux des tâches les plus fondamentales sont la régression et la classification. Bien que ces deux approches visent à faire des prédictions, elles servent des objectifs différents et s'appliquent à des types de problèmes distincts.

## 2. La Régression

### 2.1 Qu'est-ce que la régression ?

La régression est une technique de Machine Learning qui permet de **prédire une valeur numérique continue**. L'objectif est d'établir une relation mathématique entre des variables d'entrée (features) et une variable de sortie continue.

### 2.2 Types de régression

1. **Régression linéaire simple**
   - Une seule variable d'entrée
   - Relation linéaire : y = ax + b
   - Exemple : prédire le prix d'une maison basé uniquement sur sa surface

2. **Régression linéaire multiple**
   - Plusieurs variables d'entrée
   - y = a₁x₁ + a₂x₂ + ... + aₙxₙ + b
   - Exemple : prédire le prix d'une maison basé sur la surface, le nombre de chambres, la localisation

3. **Régression polynomiale**
   - Relation non linéaire
   - y = ax² + bx + c
   - Utile pour les relations plus complexes

### 2.3 Exemple pratique de régression

```python
import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt

# Données d'exemple
X = np.array([[1], [2], [3], [4], [5]])
y = np.array([2, 4, 5, 4, 5])

# Création et entraînement du modèle
model = LinearRegression()
model.fit(X, y)

# Prédictions
y_pred = model.predict(X)

# Visualisation
plt.scatter(X, y, color='blue', label='Données réelles')
plt.plot(X, y_pred, color='red', label='Prédictions')
plt.xlabel('Variable X')
plt.ylabel('Variable Y')
plt.title('Exemple de Régression Linéaire')
plt.legend()
plt.show()
```

### 2.4 Quand utiliser la régression ?

- Prédiction de valeurs continues
- Exemples d'applications :
  - Prédiction de prix (immobilier, actions)
  - Prévision des ventes
  - Estimation de la consommation d'énergie
  - Prédiction de températures
  - Analyse de séries temporelles

## 3. La Classification

### 3.1 Qu'est-ce que la classification ?

La classification est une technique qui permet de **prédire une catégorie** ou une classe parmi un ensemble prédéfini. L'objectif est d'identifier à quelle classe appartient une nouvelle observation.

### 3.2 Types de classification

1. **Classification binaire**
   - Deux classes possibles
   - Exemple : spam/non-spam, malade/sain

2. **Classification multiclasse**
   - Plus de deux classes
   - Exemple : classification d'espèces de fleurs

3. **Classification multilabel**
   - Une observation peut appartenir à plusieurs classes
   - Exemple : tags d'une image

### 3.3 Exemple pratique de classification

```python
from sklearn.datasets import make_classification
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report
import seaborn as sns

# Création d'un dataset synthétique
X, y = make_classification(n_samples=100, n_features=2, n_classes=2, random_state=42)

# Split des données
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Création et entraînement du modèle
clf = LogisticRegression()
clf.fit(X_train, y_train)

# Prédictions et évaluation
y_pred = clf.predict(X_test)
print(classification_report(y_test, y_pred))

# Visualisation
plt.figure(figsize=(10, 6))
plt.scatter(X[:, 0], X[:, 1], c=y, cmap='viridis')
plt.title('Visualisation de la Classification')
plt.xlabel('Feature 1')
plt.ylabel('Feature 2')
plt.colorbar(label='Classe')
plt.show()
```

### 3.4 Quand utiliser la classification ?

- Prédiction de catégories discrètes
- Exemples d'applications :
  - Détection de fraude
  - Diagnostic médical
  - Reconnaissance d'images
  - Analyse de sentiment
  - Filtrage de spam

## 4. Comparaison Régression vs Classification

### 4.1 Principales différences

| Caractéristique | Régression | Classification |
|-----------------|------------|----------------|
| Type de sortie | Valeur continue | Catégorie discrète |
| Métrique d'évaluation | MSE, RMSE, MAE | Accuracy, Precision, Recall, F1-Score |
| Fonction de perte | Erreur quadratique | Log loss, Hinge loss |
| Visualisation | Courbe de régression | Matrice de confusion |

### 4.2 Comment choisir ?

1. **Nature de la variable cible**
   - Continue → Régression
   - Discrète → Classification

2. **Objectif du problème**
   - Prédire une quantité → Régression
   - Catégoriser → Classification

3. **Exemples concrets**
   - Prix de maison → Régression
   - Type de fleur → Classification
   - Température → Régression
   - Diagnostic médical → Classification

## 5. Bonnes pratiques

### 5.1 Préparation des données
- Nettoyage des données
- Gestion des valeurs manquantes
- Normalisation/Standardisation
- Feature engineering

### 5.2 Évaluation du modèle
- Split train/test
- Validation croisée
- Métriques appropriées
- Analyse des erreurs

### 5.3 Optimisation
- Sélection de features
- Tuning des hyperparamètres
- Gestion du surapprentissage
- Validation des résultats

## 6. Ressources et outils

### 6.1 Bibliothèques Python
- scikit-learn
- statsmodels
- TensorFlow
- PyTorch

### 6.2 Ressources d'apprentissage
- Documentation scikit-learn
- Cours en ligne (Coursera, edX)
- Kaggle competitions
- Articles scientifiques

## 7. Exercices pratiques

1. **Régression**
   - Prédiction de prix immobiliers
   - Analyse de séries temporelles
   - Estimation de consommation énergétique

2. **Classification**
   - Classification d'emails (spam/non-spam)
   - Reconnaissance de chiffres manuscrits
   - Prédiction de défaut de paiement

## 8. Conclusion

La compréhension de la différence entre régression et classification est fondamentale en Machine Learning. Le choix entre les deux dépend de la nature du problème et du type de prédiction souhaité. Une bonne maîtrise de ces concepts permet de :
- Choisir la bonne approche pour chaque problème
- Sélectionner les métriques appropriées
- Optimiser les modèles efficacement
- Interpréter correctement les résultats 