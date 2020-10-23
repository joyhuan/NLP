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
