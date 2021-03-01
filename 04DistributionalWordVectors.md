## Distributional Word Vectors 
### Motivation for word embeddings 
Variability (multiple forms, similar meaning)

### How should we embed words? 
distribution hypothesis: words that appear in similar contexts have similar meanigns (Joos, 1950; Harris, 1954; Firth, 1957)

![Image of word embedding table](https://github.com/joyhuan/NLP/blob/main/images/word_embedding.png)

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
    - vector entry is then tf * idf
- Pointwise Mutual Information (PMI)
    - consider two rvs, X and Y 
    - do two events X = x and Y = y occur together more often than if they were independent? 
    - if independent, PMI = 0
![Image of word embedding table](https://github.com/joyhuan/NLP/blob/main/images/PMI_word_vectors.png)
    - Positive PMI? 
        - some have found benefit by truncating PMI at 0 ("positive PMI")
        - negative PMI: words occur toghether less than we would expect, i.e., they are anticorrelated 
        - these anticorrelations may need more data to reliably estimate 
        - however, negative PMIs do seem reasonable! 

### Summary 
- word vectors: the use of a vector of numbers to represent a word 
- distributional word vectors: the use of distributional statistics (eg, word co-occurence counts) in defining word vectors 
- different window sizes lead to different kinds of similarity in the vectors
- many options for computing similarity of two vectors: 
    - dot product is a simple starting point 
    - cosine similarity accounts for vector length and works better for word vectors 
- simple distributional vectors are ok, but modifying counts can help 
- one method: scale down counts for common context words, usually with a variant of inverse document frequency (idf)
- another method: pointwise mutual information (PMI)
- PMI provides information about whether two events are independent 
- view center and context word slots as random variables; words are events/outcomes of those random variables 
- use PMI (center word, context word) values in place of counts for better word vectors