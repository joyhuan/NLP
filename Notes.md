# Notes (Kevin Gimpel NLP)
## 01 | What is natural language processing?
a subarea of computer science that includes problems and solutions related to human language 

### Problem categories 
#### User-Facing Applications (Everyday life) 
  - Text Classification (spam/priority/category)
  - Text Completion/Auto complete 
  - Machine Translation 
  - Personal Assistants (Siri/Alexa)
  - Speech recognition/web search 
#### Supporting Technologies (may help better design user-facing applications)
  - Part-of-Speech Tagging 
  - Constituency Parsing 
  - Dependency Parsing 
  - Semantic Role Labeling 
  - Coreference Resolution 
  - Named Entity Recognition 
#### Language Understanding Capabilities 
  - Winograd Schema Coreference Resolution 
  - Reading Comprehension Question Answering 
  - Natural Language Inference

### Solutions/A Brief History of NLP 
- classical NLP: 1960s - early 1990s 
  - linguistic theory, manually-defined rules 
  - small-scale datasets and limited experimentation 
  
- statistical NLP: late 1980s - 2013 
  - supervised machine learning with annotated datasets
  - (mostly) linear models with manually-defined features
  - linguistic knowledge used in annotation, features, etc. 
  
 - neural NLP: 2012 - present 
  - focus is on learning representations of language from large text corpora with deep neural networks 
  - less hand crafting of features/ use of linguistic structure 
  
### Why is NLP hard? 
  - Ambiguity: one form can have multiple meanings 
  - Variability: multiple forms can have the same meaning 

### Roadmap
  - words: tokenization, morphology, lexical semantics 
  - text classification 
  - language modeling and neural language models 
  - word embeddings 
  - recurrent/recursive/convolutional networks in NLP
  - sequence labeling, HMMs, dynamic programming 
  - syntax and syntactic parsing 
  - attention and transformers
  - machine translation and other NLP tasks. 
  
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

## 03 | Morphology
### morpheme: the smallest meaning-bearing unit in a language 
- types of morphemes: 
  - stem: a core meaning-bearing unit 
  - affix: a piece that attaches to a stem, adding some function or meaning 
### morphology: the study of how words are built from morephemes 
### Kinds of Word Formation
- inflectin: modifying a word with an affix to change its grammatical function (tense, number, etc.)
  - result is another form of the same word
    book -> books walk -> walked 
- derivation: adding an affix to a word to create a new word 
    great -> greatly great -> greatness 
- compounding: combining two words 
    lawsuit, keyboard, bookcase 
### Morphological Decomposition 
- usually, morphological decomposition is simply spliting a word into its morphemes 
- but it can actually be a hierarchical structure 
    - unbreakable -> (un) break able
- ambiguity in hierarchical morphological decomposition? 
  - rare, but it does happen 
  - eg: unlockable 
    - (un + lock) + able: "able to be unlocked"
    - un + (lock + able): "not able to be locked"
- NLP problems that address morphology: 
  - lemmatization 
  - stemming 
### Terminology 
  - lemma
    - canonical/dictionary form of a word 
    - words with same lemma have same stem, part of speech, rough semantics 
  - wordform 
    - full inflected or derived form of a word as it appears in text 
### lemmatization: convert wordform to lemma 
  - mostly about finding the correct dictionary entry, but this may depend on the context 
### stemming: reduce words to their stems by removing affixes 
    - usually implemented with language-specific, manually-designed rules 
    - commonly used in information retrieval 
    - Porter's Algorithm (the most common English stemmer)
      - Step 1a 
        - sses -> ss caresses -> caress 
        - ies -> i ponies -> poni 
        - ss -> ss caress -> caress 
        - s -> null cats -> cat 
      - Step 1b 
        - (*v*)ing -> null walking -> walk, sing -> sing 
        - (*v*)ed -> null plastered -> plaster 
### Lemmatization vs. Stemming 
  - Lemmatization 
    - viewed as an NLP task 
    - solved with dictionary look-up, possibly with machine learning 
  - Stemming uses manually-defined rules 
    - simple and fast, but limited due to reliance on rules 
    - may conflate words erroneously 
  - Both may remove information 
    - To mitigate, combine lemma/stem form with original form, use both! 
    
### Data-Driven Segmenters 
  - segment words into pieces (subword units or wordpieces) based on common character sequences in a dataset 
  - most popular methods: 
    - Byte pair encoding (BPE)
    - SentencePiece's unigram langauge model (LM)
  - these are efficient and effective, but they don't necessarily correspond to morphology; splits may be arbitrary 
  - very popular when using neural networks (BERT, GPT, etc)
### Bype Pair Encoding (BPE) (Gage, 1994)
- simple data compression technique 
- iteratively replaces most frequent pair of bytes in a sequence with a single, unused byte 
- Sennich et al. (2016) adapted BPE for segmenting words 
- "merge": operation that combines two consecutive units into a single unit
  - initially, units are characters (e.g., s or t)
  - after merges, units become character sequences (eg., st or books)
- greedy algo: 
  - merge 2 units with the largest 2-unit sequence count, produce merged unit 
  - replace all instances of that 2-unit sequence with the merged unit, recompute counts 
### Summary 
- morphology: study of how words are built from morphemes 
- morphemes: meaning-bearing units in a language, often classified into stems and affixes 
- type/token ratio correlated with morphological richness of a language 
- types of word formation: inflection, derivation, compounding 
- morphological decomposition is sometimes hierarchical (unlockable)
- lemmatization: convert wordform to lemma (may depend on context)
- stemming: removing affixes from words to get stems (simple, rule-based)
- data-driven segmentation (BPE, unigram LM) split words based on data, very common in deep learning
