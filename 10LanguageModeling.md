## 10 Language Modeling
### Language Modeling
- assign probabilities to token sequences
- why? 
    - machine translation:
        - P(turn the camera off) > P(put the camera out)
    - speech recognition:
        - P(be back soonish) > P(be bassoon dish)
    - spelling/grammar correction:
    - assistive writing, dialogue systems, question answering, etc
- goal: compute the probability of a sequence of words:
![Image of language model](https://github.com/joyhuan/NLP/blob/main/images/language_model.png)
### Chain Rule 
- factor joint probability into product of conditional probabilities
- we have not yet made any independence assumptions
### Importatn Detail: Modeling Length
- a language model assigns probs to token sequences x 
    - x can be any length, so the probs should sum to 1 across all possible sequences of all possible lengths
- usually length is modeled by including a "stop symbol" `</s>` at the end of the sequence and using "stopping probs"
    - a "start symble"`<s>` is also assumed to be at the beginning 
- our language model with start/stop symbols
![Image of language model with start/stop symbols](https://github.com/joyhuan/NLP/blob/main/images/start_stop_symbol.png)
### Why Stopping Probs?
- need to ensure sum of probs = 1
- consider removing stopping probs
### Without Stopping Probs
### Other Ways of Modeling Length
- alternatively, we can model the length n explicitly (e.g., using a zero-truncated Poisson distrubtion)
![Image of explicit length](https://github.com/joyhuan/NLP/blob/main/images/explicit_length.png)
### #stimating Language Model Probs
- let's use maximum likelihood estimation(MLE)
- problem: we'll never have enough data!
### Independence Assumption
- approximate each conditional prob by conditioning on only the most recent k words
### n-gram Language Models
### Estimating Bigram Prob
### Evaluating Language Models
- extrinsic(task-based) evaluation
    - use LM in a system for some task, see if performance improves
    - downsides:
        - can be time-consuming depending on task/system
        - changing the LM might require changing how it's used in the system in order to improve performance
- intrinsic evaluation
    - compute prob of held-out data
    - standard metric: perplexity
    - downside:
        - may not correlate with system performance on downstream tasks
### Prob of Held-out Data
![Image of held-out data](https://github.com/joyhuan/NLP/blob/main/images/held_out_data.png)
### Prob -> Perplexity
- the lower the perplexity, the better the model
### Perplexity as Branching Factor
