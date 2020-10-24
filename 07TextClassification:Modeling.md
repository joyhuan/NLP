## 07 Text Classification: Modeling
### Features for NLP
- NLP datasets include inputs and ouputs 
- features are usually not included 
- you have to define your own featrues 
- contrast this with UCI datasets, which include feature vectors 
### Defining Features
- this is a large part of NLP 
- since 1995: feature engineering 
- since 2012: representation learning 
### Feature Engineering 
- often decried as "costly, hand-crafted, expensive, domain-specific", etc.
- but in practive, simple features account for most of the accuracy 
- and there's still engineering required in representation learning 
### Unigram Binary Features 
- two example features: 
f_1(x, y) = I[y = positive] ^ I[x contains great] 

f_2(x, y) = I[y = negative] ^ I[x contains great] 
- we usually think in terms of feature templates 
- unigram binary feature template:
f^{u,b}(x,y) = I[ y=label] ^ I[x contains word]
- to create features, this feature template is instantiated for particular labels and words

### Features in ML vs. NLP 
- UCL ML datasets: 
    - fixed-length dense feature vector for every instance 
    - number of features typically a few hundred to a few thousand 
- NLP datasets: 
    - define your own feature templates, instantiate millions of features using them 
    - feature vectors for each instance are sparse
### Unigram Count Features 

### Higher-Order Feature Templates

### Feature Count Cutoffs 

- all of our features include an indicator for a particular label
- this may be different from what you're used to 
    - when using dense feature vectors in ML, the ML algo may create weights for every ouput label for every feature 
    - that is, you specify a feature like: f_3(x) = I[x contians great]
    - and then the ML code creates weights for all lables for this feature