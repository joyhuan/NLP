## Distributional Word Vectors 
### Motivation for word embeddings 
Variability (multiple forms, similar meaning)

### How should we embed words? 
distribution hypothesis: words that appear in similar contexts have similar meanigns (Joos, 1950; Harris, 1954; Firth, 1957)

![Image of word embedding table](https://github.com/joyhuan/NLP/blob/main/word_embedding.png)

- once we have word vectors, we can compute similarities! 
- many ways to define similarity of two vectors
- a simple way: dot product (also called inner product)
- with dot product as similarity function, let's find the most similar words ("nearest neighbors") to each word 
- dot product is large when the vectors have very large (or very negative) values in the same dimenstions
- cosine similarity! 

### Improving Counts 
- counts of common words ("the") are very large, but not very useful 
- many ways proposed for improving raw counts 
- tf-idf ("term frequency-inverse document frequency")
    - tf is just the count of the two words 
    - idf is computed for the context word 
        - document frequency = number of documents in which a word appears 
        - inverse of document frequency will be small for common words 
        
