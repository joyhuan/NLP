## 05 Word Sense and Lexical Semantics 
- Variability: multiple forms, one meaning -> merge forms 
- Ambiguity: one form, multiple meanings -> split form 
### Word Sense 
- sense(or word sense): a discrete representation of an aspect of a word's meaning 
- one lemma bank can have multiple senses 
- ways to categorize the patterns of multiple meanings of words: 
    - homonymy: the multiple meanings are unrelated (concidental?)
    - polysemy: the multiple meanings are related 
    - many non-reate words have multiple senses, but sometimes the senses are very similar 
### Synonyms 
- informally: words with same meaning in some or all contexts 
- two words are synonyms if they can be substituted for each other in all situations 
- few (or no) examples of perfect synonymy 
    - even if many aspects of meaning are identical 
    - still may not preserve the acceptability based on notions of politeness, slang, register, genre, etc. 
- Synonymy is a relation between senses rather than words 
### Antonymy
- antonyms: senses that are opposites wrt one feature of meaning
- otherwise, they are very similar! 
- can be difficult to distinguish synonyms and antonyms with data-driven methods (eg, distributional word vectors)
### Hyponymy and Hypernymy
- sense A is a hyponym of sense B is A is more specific, denoting a subclass of B 
- conversely: hypernym ("hyper is super")
### WordNet(Fellbaum, 1998)
- hierarchically organized lexical database
- fine-grained sense inventories, relationships among senses
- originally developed for English; other languages now available 
- English WordNet version 3.0 contains:
    - Noun 117,798
    - Verb 11,529
    - Adj 22,479
    - Adv 4,481
- How is "sense" defined in WordNet?
    - synset (synonym set):
        - set of near-synonyms, instantiates a sense or concept 
        - Variability: the three senses of fool belong to different synsets
        - Ambiguity: each synset contains senses of several different words
- Word Sense Disambiguation (WSD)
    - given: 
        - an ambiguous word in context 
        - a fixed inventory of potential word senses 
    - choose the correct sense based on the context
- How to solve WSD? 
context 
- Role of WSD?
    - many WSD systems have been developed since the 1990s 
    - researchers hoped that WSD systems would be useful for tasks like machine translation, question answering, sentiment analysis, etc.
    - unclear if a separate system is needed 
    - trend today: end-to-end modeling that disambiguates word sense as part of translation, question answering, etc. 
### Symmary 
- WordNet: dictionary organized according to synonym sets("synsets"), with semantic relationships (antonymy, hyponymy, etc.)
- word sense disambiguation(WSD): NLP task of determining intended sense of a word based on its context
    - methods use words from context of the ambiguous word 
    - unclear if useful for downstream tasks 
    - today often done implicitly as part of another task