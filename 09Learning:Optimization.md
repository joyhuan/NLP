## 09 Learning: Optimization
### Gradient Descent
### Stochastic Gradient Descent (SGD)
- like gradient descent, except makes updates more frequently, using gradients computed from a small subset of the data (a "mini-batch")
    - "stochastic" refers to it being a stochastic approximation to gradient descent 
- applicable when objective function is a sum
- converges much faster than gradient descent
- many popular variants that choose/update parameter-specific step sizes: Adam, SGD+momentrum, AdaGrad, etc. 
### What if F is not differentiable?
- some loss functions are not differentiable(perception, hinge loss)
- but they are subdifferentiable, so we can compute subgradients and use (stochastic) subgradient descent
### Subderivatives
- slope of line that touches the functionm at a point and is either touching/lying below ("sub") the function everywhere else
- can be multiple subderivatives at a point
- a convex function g is differentiable at point x0 iff the subdifferential of g at x0 contains only the derivative of g at x0
### Stochastic Subgradient Descent (SSD)
- just like stochastic gradient descent, except replace gradients with subgradients
- similar theoretical guarantees
### Calculating Subgradients
- at points of differentiability, just use your rules for calculating gradients
- at points of nondifferentiability, just find a single subgradients; any subgradients will do
### Perceptron Loss with Regularization
- update rule with L2 regularization:
    - pushes weights closer to 0 ("weight decay")
### Perceptron -> Hinge
### Hinge Loss Subgradients for Linear Models
- "cost-augmented inference/decoding"
![Image of optimization functions](https://github.com/joyhuan/NLP/blob/main/optimization.png)