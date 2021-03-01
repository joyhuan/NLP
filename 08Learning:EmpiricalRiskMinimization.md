## 08 Learning: Empirical Risk Minimization
### Learning: How do we choose the weights w? 

Learning: Empirical Risk Minimization

alpha ease_of_use + beta effectiveness + gamma applicability 
(for some positive constants alpha, betam gamma)

### Cost Functions
- compares two labels, usually a predicted label and a gold standard
- should be as similar as possible to the evaluation metric for the task 
- usual conventions: 
    - cost(y,y) = 0 
    - cost(y,y') = cost(y',y)
- 5-way sentiment classification 
L = {very negative, negative, neutral, positive, very positive}
- when evaluating classifiers for this task, we may want to differentiate among types of errors 
- cost function can be defined to reflect this 

### Risk Minimization 
- problem: don't know P the distribution

### Empirical Risk Minimization 
- solution: replace expectation with a sum over examples 
- problem: NP-hard even for binary classification with linear models 
- solution: replace "cost loss" (also called "0-1" loss) with a surrogate function that is easier to optimize 

### SUrrogate Loss Functions 
- why is this so difficult to optimize? 
- not necessarily continuous, can't use gradient-based optimization 

- max-score loss: loss_maxscore(x,y,w) = -score(x,y,w)
- perceptron loss: (underlying perceptron algo)
![Image of loss functions](https://github.com/joyhuan/NLP/blob/main/images/loss_fcns.png)
- hinge loss: (underlying support vector machines, can be shown to be an upper bound on the cost loss)