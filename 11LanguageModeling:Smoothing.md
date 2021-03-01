## 11 Language Modeling: Smoothing
### Smoothing
better handling for the rare events
### "Add-1" estimation
- just add 1 to all counts!
- also called Laplace smoothing
- simple and avoids zeros, but doesn't work as well as other methods
### Backoff and Interpolation
- use multiple n-gram sizes in the same language model
- backoff:
    - use trigram model if its prob is nonzero
    - otherwise, use bigram model if its prob is nonzero
    - otherwise, use unigram
- interpolation:
    - mixture of unigram, bigram, and trigram models
- interpolation tends to work better
### Linear Interpolation
- estimate unigram/bigram/trigram models using MLE, then combine them
- lambdas can be estimated using development data
- they can also be a function of the context
- intuitively, may want lambda_3(x',x'') to be larger if count(x',x'') is large
### Kneser-Ney Smoothing
- widely used and effective
- a few components:
    - absolute discounting
    - interploation with continuation probs
- best variant seems to be "modified Kneser-Ney" -- see Chen and Goodman(1998)
### Absolute Dsicounting
- observed bigrams have counts that are overestimated
- unobserved bigrams have counts that are underestimated
- subtract d from each numerator count
- use original counts for denominator
- so there's some "missing prob mass"
- lambda function is defined to make things normalize correctly
### Continuation Probs
- unigram prob is most useful when we haven't seen bigram
- instead of unigram P(x), use P_continuation(x)
- How likely is x to be a novel continuation?
- normalize by total number of bigram types
### Kneser-Ney Smoothing
- Interpolated Kneser-Ney:
![Image of Kneser-Ney Smoothing](https://github.com/joyhuan/NLP/blob/main/images/Kneser-Ney.png)
- this is the bigram version; recursive versions exist for higher orders
### Smoothing for Web-scale Models
- "Stupid backoff" (Brants et al., 2007) 
![Image of Stupid backoff](https://github.com/joyhuan/NLP/blob/main/images/stupid_backoff.png)
### Close Vocabulary
- if there are unknown words in the test data, smoothing does not help
    - prob of test data is still zero
- we must know the full vocab ahead of time(for both training and held-out data!)
### Open Vocab
- create an unknown word symbol "<UNK>"
- at training time:
    - replace some rare words with <UNK>
    - then estimate probs as though <UNK> is a normal word
- at test time:
    - replace unknown words with <UNK>
- when comparing open-vocab language models, make sure the vocab match!
- favors smaller vocab (small perplexity but useless)