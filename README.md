
# Text Preprocessing

1. Noise Removal 
```
strip HTML tags
```

2. Tokenization
```
breaking text into words
```

3. Normalization
* Stemming : chp off word prefixes and suffixes
* Lemmatization: bring words to theirs root forms
```
cleaning text data
```

---

# Settings Up

```
python -m pip install nltk
import nltk
nltk.download()

C:\nltk_data (Windows), 
/usr/local/share/nltk_data (Mac), 
/usr/share/nltk_data (Unix).
```

# Parsing Text
Parsing is an NLP process concerned with segmenting text based on syntax.

### Parsing method
1. Part-of-speech tagging (POS tagging) identifies parts of speech (verbs, nouns, adjectives, etc.). 
   NLTK can do it faster (and maybe more accurately) than your grammar teacher.
2. Named entity recognition (NER) helps identify the proper nouns (e.g., “Natalia” or “Berlin”) in a text. 
   This can be a clue as to the topic of the text and NLTK captures many for you.
3. Dependency grammar trees help you understand the relationship between the words in a sentence. 
   It can be a tedious task for a human, so the Python library spaCy is at your service, even if it isn’t always perfect.
4. Regex parsing, using Python’s re library, allows for a bit more nuance. 
   When coupled with POS tagging, you can identify specific phrase chunks. On its own, it can find you addresses, emails, and many other common patterns within large chunks of text.

# Language Models: Bag-of-Words
When grammar and word order are irrelevant, this is probably a good model to use.
```
{"the": 2, "squid": 1, "jump": 1, "out": 1, "of": 1, "suitcase": 1}
```

# Language Models: N-Gram and NLM

```
the n-gram model considers a sequence of some number (n) units and calculates the probability of each unit in a body of language given the preceding sequence of length n. 
```

```
“The squids jumped out of the suitcases. The squids were furious.”

{('', 'the'): 2, ('the', 'squids'): 2, ('squids', 'jumped'): 1, ('jumped', 'out'): 1, ('out', 'of'): 1, ('of', 'the'): 1, ('the', 'suitcases'): 1, ('suitcases', ''): 1, ('squids', 'were'): 1, ('were', 'furious'): 1, ('furious', ''): 1}
```

Neural Language Models
* LSTMs
* transformer models

# Topic Models 

* area of NLP dedicated to uncovering latent, or hidden, topics within a body of language
* A common technique is to deprioritize the most common words and prioritize less frequently used terms as topics in a process known as term frequency-inverse document frequency (tf-idf).
    * sklearn
    * gensim

* Whether you use your plain bag of words (which will give you term frequency) or run it through tf-idf, the next step in your topic modeling journey is often latent Dirichlet allocation (LDA). LDA is a statistical model that takes your documents and determines which words keep popping up together in the same contexts (i.e., documents).
  
* If you have any interest in visualizing your newly minted topics, word2vec is a great technique to have up your sleeve. word2vec can map out your topic model results spatially as vectors so that similarly used words are closer together. In the case of a language sample consisting of “The squids jumped out of the suitcases. The squids were furious. Why are your suitcases full of jumping squids?”, we might see that “suitcase”, “jump”, and “squid” were words used within similar contexts. This word-to-vector mapping is known as a word embedding.

# Text Similiarty 

text similarity — including spelling correction — is a major challenge within natural language processing.

Addressing word similarity and misspelling for spellcheck or autocorrect often involves considering the Levenshtein distance or minimal edit distance between two words. The distance is calculated through the minimum number of insertions, deletions, and substitutions that would need to occur for one word to become another. For example, turning “bees” into “beans” would require one substitution (“a” for “e”) and one insertion (“n”), so the Levenshtein distance would be two.

It’s also helpful to find out if texts are the same to guard against plagiarism, which we can identify through lexical similarity (the degree to which texts use the same vocabulary and phrases). Meanwhile, semantic similarity (the degree to which documents contain similar meaning or topics) is useful when you want to find (or recommend) an article or book similar to one you recently finished.

