# Introduction au Traitement du Langage Naturel (NLP)

## 1. Qu'est-ce que le NLP ?

Le Traitement du Langage Naturel (Natural Language Processing - NLP) est une branche de l'Intelligence Artificielle qui permet aux machines de **comprendre**, **interpréter** et **générer** le langage humain. Cette technologie est au cœur de nombreuses applications modernes que nous utilisons quotidiennement.

### 1.1 Importance du NLP

- **Communication Homme-Machine** : Facilite l'interaction naturelle avec les systèmes
- **Automatisation** : Traitement automatique de grandes quantités de textes
- **Analyse** : Extraction d'informations et de connaissances à partir de textes
- **Génération** : Création de contenu textuel cohérent et pertinent

### 1.2 Applications courantes

1. **Assistants virtuels**
   - Siri, Alexa, Google Assistant
   - Chatbots
   - Systèmes de support client

2. **Analyse de texte**
   - Analyse de sentiment
   - Classification de documents
   - Extraction d'informations

3. **Traduction automatique**
   - Google Translate
   - DeepL
   - Systèmes de traduction en temps réel

## 2. Concepts fondamentaux du NLP

### 2.1 Prétraitement du texte

1. **Tokenization**
   - Découpage en mots/tokens
   - Gestion de la ponctuation
   - Traitement des caractères spéciaux

```python
from nltk.tokenize import word_tokenize

texte = "Le NLP est fascinant ! Il permet de nombreuses applications."
tokens = word_tokenize(texte)
print(tokens)
# ['Le', 'NLP', 'est', 'fascinant', '!', 'Il', 'permet', 'de', 'nombreuses', 'applications', '.']
```

2. **Normalisation**
   - Mise en minuscules
   - Suppression des accents
   - Standardisation du format

3. **Suppression des stop words**
   - Mots très fréquents et peu informatifs
   - Articles, prépositions, etc.

```python
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

stop_words = set(stopwords.words('french'))
texte = "Le chat noir dort sur le canapé"
tokens = word_tokenize(texte)
filtered = [mot for mot in tokens if mot.lower() not in stop_words]
print(filtered)
# ['chat', 'noir', 'dort', 'canapé']
```

### 2.2 Représentation du texte

1. **Sac de mots (Bag of Words)**
   - Comptage simple des mots
   - Perte de l'ordre des mots
   - Utilisé pour la classification basique

```python
from sklearn.feature_extraction.text import CountVectorizer

vectorizer = CountVectorizer()
corpus = [
    "Le chat mange",
    "Le chien dort",
    "Le chat dort"
]
X = vectorizer.fit_transform(corpus)
print(vectorizer.get_feature_names_out())
print(X.toarray())
```

2. **TF-IDF (Term Frequency-Inverse Document Frequency)**
   - Importance relative des mots
   - Prend en compte la fréquence dans le document et le corpus

```python
from sklearn.feature_extraction.text import TfidfVectorizer

vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(corpus)
print(vectorizer.get_feature_names_out())
print(X.toarray())
```

3. **Word Embeddings**
   - Word2Vec, GloVe, FastText
   - Représentation vectorielle dense
   - Capture les relations sémantiques

```python
from gensim.models import Word2Vec

# Préparation des données
sentences = [["le", "chat", "mange"], ["le", "chien", "dort"]]
model = Word2Vec(sentences, vector_size=100, window=5, min_count=1)

# Similarité entre mots
print(model.wv.similarity('chat', 'chien'))
```

## 3. Techniques avancées

### 3.1 Modèles de langage

1. **RNN (Recurrent Neural Networks)**
   - LSTM (Long Short-Term Memory)
   - GRU (Gated Recurrent Unit)
   - Traitement séquentiel du texte

2. **Transformers**
   - Architecture basée sur l'attention
   - BERT, GPT, T5
   - État de l'art en NLP

### 3.2 Applications pratiques

1. **Analyse de sentiment**
```python
from transformers import pipeline

# Création du pipeline
classifier = pipeline('sentiment-analysis', model='nlptown/bert-base-multilingual-uncased-sentiment')

# Analyse
texte = "Ce produit est vraiment excellent !"
resultat = classifier(texte)
print(resultat)
```

2. **Génération de texte**
```python
from transformers import pipeline

generator = pipeline('text-generation', model='gpt2')
texte = "L'intelligence artificielle va"
resultat = generator(texte, max_length=50, num_return_sequences=1)
print(resultat[0]['generated_text'])
```

## 4. Bonnes pratiques en NLP

### 4.1 Préparation des données
- Nettoyage rigoureux du texte
- Gestion des cas spéciaux
- Validation des données

### 4.2 Choix du modèle
- Adaptation à la tâche
- Considération des ressources
- Équilibre performance/complexité

### 4.3 Évaluation
- Métriques appropriées
- Validation croisée
- Tests sur différents types de textes

## 5. Défis et considérations

### 5.1 Défis techniques
- Ambiguïté du langage
- Gestion des expressions idiomatiques
- Multilingue et variations culturelles

### 5.2 Considérations éthiques
- Biais dans les données
- Respect de la vie privée
- Utilisation responsable

## 6. Outils et ressources

### 6.1 Bibliothèques Python
- NLTK
- spaCy
- Transformers (Hugging Face)
- Gensim
- TextBlob

### 6.2 Ressources d'apprentissage
- Documentation officielle des bibliothèques
- Cours en ligne spécialisés
- Communautés NLP
- Datasets publics

## 7. Exercices pratiques

1. **Analyse basique**
   - Tokenization et nettoyage
   - Analyse de fréquence
   - Visualisation de données textuelles

2. **Projets intermédiaires**
   - Classification de textes
   - Analyse de sentiment
   - Extraction d'entités nommées

3. **Projets avancés**
   - Chatbot simple
   - Système de résumé automatique
   - Traduction basique

## 8. Conclusion

Le NLP est un domaine en constante évolution qui offre de nombreuses possibilités d'applications. Les concepts fondamentaux présentés ici constituent une base solide pour :
- Comprendre les enjeux du traitement automatique du langage
- Développer des applications pratiques
- Suivre les évolutions du domaine
- Contribuer à l'innovation en IA 