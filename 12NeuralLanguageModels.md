## 12 Neural Language Models
- idea: use a neural network for n-gram language modeling: P(x|x',x'')
### What is a neural network?
- continuous function with learnable parameters
    - usually inputs and outputs are vectors
    - typically a nonlinear function
- neural networks/deep learning is best thought of as a modeling strategy that combines:
    - distributed representations(eg. word embeddings)
    - representation learning
    - nonlinear functions
### A Simple Neural Trigram Language Model
![Image of Neural Network](https://github.com/joyhuan/NLP/blob/main/images/neural_net.png)
- output is a vector s containing probs of all possible next words
- to get s, do matrix multiplication of parameter matrix W and input, then "softmax" transformation

![Image of Fully Connected Layer](https://github.com/joyhuan/NLP/blob/main/images/fully_connected_layer.png)
### Softmax
- function that maps a vector v of real values (called "logits" or "scores") to a vector p of probs:

    - exponentiate scores(this makes them positive), then normalize to get probs
- using scalar notation (computing a single prob p_i):
![Image of Softmax](https://github.com/joyhuan/NLP/blob/main/images/images/softmax.png)
- what are the dimensionalities?

![Image of Dimensionalities](https://github.com/joyhuan/NLP/blob/main/images/dimensionalities.png)
- what are the parameters in this model?
- how many total params are in this model?
![Image of Parameters](https://github.com/joyhuan/NLP/blob/main/images/neural_params.png)
### Comparing Models of P(x|x',x'')
![Image of Comparison](https://github.com/joyhuan/NLP/blob/main/images/compare_trigram_neural.png)
![Image of Formula](https://github.com/joyhuan/NLP/blob/main/images/neural_formula.png)
![Image of Hidden Layer](https://github.com/joyhuan/NLP/blob/main/images/hidden_layer.png)
- g functions:
    - (logistic) sigmoid (bounded between 0 and 1)
    - rectified linear unit(ReLU) y = max(0,x)
### Why nonlinearities?
network with 1 hidden layer: 

h' = W'h + b'

h = g(Wx + b)
- if g is linear, then we can rewrite the above as a single affine transfromation (use distributivity of matrix multiplication)
- so, to benefit from multiple layers, we need some kind of nonlinearity
### What's next?
- How do we efficiently compute gradients for learning with neural networks?
- What other kinds of "neural layers" are commonly used?
- How do neural networks fit into our classified framework?
- How do we choose the number of hidden layers, their dimensionalities, and the nonlinearity?