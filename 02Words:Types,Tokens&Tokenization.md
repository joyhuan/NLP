## 02 | Words: Types, Tokens, & Tokenization 
###  Tokenization: convert sequence of characters into sequence of tokens 
- Center tokenizer 
- most tokenizers are rule-based 
- several conventions 
- important to be consistent across NLP systems, match tokenization of external tools/resources 
- see nltk.tokenize(also for sentence tokenization)
- Chinese, Japanese, Thai: no spaces between words 
- Tokenization becomes highly non-trivial! 
- Multiple conventions: 
- tokenization usually only adds whitespace 
- might we also want to remove whitespace? 
  - names: New York -> NewYork? 
  - non-compositional compounds: hot dog -> hotdog? 
  
### type: a unique word (an entry in a vocabulary or dictionary)

### token: an instance of a type in a corpus 

### useful statistic: type/token ratio 

### How does the type/token ratio change when adding more data? 
more data -> lower type/token ratio 
### How many words are there? 
- size of vocabulary continues to grow as you collect more data 
- you'll never find all the words 
- Zipf's law: frequency of a word is inversely proportional to its rank in the word frequency list 

### The Long Tail 
- there are so many word types! 
- but words have internal structure 

### Summary
- to do NLP on some text, we need to preprocess it: 
  - tokenize documents into sentences 
  - tokenize sentences into tokens 
- rule-based tokenizers exist for many languages 
- for writing systems without whitespace, tokenization becomes complex (often treated as an NLP problem)
- useful terms: type, token, type/token ratio 
- when adding data, number of types keeps increasing 
- most types are extremely rate (Zipf's law)
- people can often understand a novel word type based on its internal structure and the context of its use 