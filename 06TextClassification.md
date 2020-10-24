## 06 Text Classification
- text classification: given an input text, label it with a category from a fixed set 
- eg: spam detection, sentiment classification, topic classification, etc.
- text classification is solved with data-driven methods 
- where does the data come from? 
- NLP datasets include inputs(usually text) and outputs (often some sort of annotation)
### Annotation 
- supervised ml needs labeled datasets, where labels are called ground truth 
- in NLP, labels are annotations provided by humans 
- there is always some disagreement among annotators, even for simple tasks
- these annotations are called a gold standard
### How are NLP datasets developed? 
1. paid, trained human annotators 
    - traditional approach
    - researchers write annotation guidelines, recruit & pay annotators (often linguists)
    - more consistent annotations, but costly to scale 
    - eg. Penn Treebank (1993)
2. crowdsourcing (eg. Amazon Mechanical Turk)
    - more recent trend (2008-present)
    - hard to train annotators, but easier to get multiple annotations for each input (which can then be averaged)
    - eg. Stanford Sentiment Treebank 
3. naturally-occuring annotation 
    - long history: used by IBM for speech recognition and statistical machine translation (There's No Data Like More Data)
    - highly useful today too, due to vast amounts of text in electronic form 
### Data for Text Classification 
- data point: (x, y)
- textual input: x
- classification label: y
### What is a classifier? 
- a function from inputs x to classification labels y
- one simple type of classifier: 
    - for any input x, assign a scalar score to each label y, parameterized by parameters w: score(x,y,w)
    - classify by choosing highest-scoring label
### Modeling, Inference, Learning 
- our classifier framework: 
![Image of word embedding table](https://github.com/joyhuan/NLP/blob/main/modeling_inference_learning.png)

- We will use this formulation throughout 
    - even when output space is exponentially large or unbounded (eg, machine translation)

### Experimental Practice 
- how should we manage our data for data-driven NLP? 
- first innovation: split into train and test 
    - motivation: simulate conditions of applying system in practice
- but, there's a problem with this ... 
    - we need to explore and evaluate methodological choices 
    - after multiple evaluations on text, it is no longer a simulation of real-world conditions
- we need to explore/evaluate methodological choices; what should we do? 
    - some use cross validation on train, but this is slow with large training sets 
- second innovation: divide data into train, test, and a thrid set called development(dev) or validation(val)
    - use dev/val to evaludate choices 
    - then, when readyto submit the paper, evaludate the best model on test 
- are we done yet? no! There's still a problem: 
    - if we have a lot of choices we're tuning, we will overfit to dev/val 
- best practice: split data into train, development(dev), development test(devtest), and test 
    - even better to have even more test sets! test1, test2, etc. 
    - dev, devtest, test, etc. do not need to be very large 
- these details are important!
    - when you publish a result, it had better be replicable without tuning anything on test data
