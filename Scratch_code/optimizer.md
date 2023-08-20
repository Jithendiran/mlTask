# Optimizers
        Optimizers are used to reduce the error rate or cost function of a model by updating the weight

# Gradient Descent

## [What is Gradient?](!https://www.youtube.com/watch?v=Yu8Yv_izi3A&t=241s)
        Differentiation is used to calculate the rate of change of a function (how quick a function is changing), rate of change is known as gradient/tangent. If the tangent is 0 means the slope at the point is flat that is the local minimum point. Gradient is used to find the maximum steep of the slope. In Deep learning need to find the minimum of the steep which is opposite of the actual one so -ve is used.

## Why it is used in Deep learning?
        Initially Neural Network's weight are init randomly and calculate the loss, these steps are run iteratively. When the loss are plot in a grap it looks like a slop of x^2, So gradient is used to calculate the tangent and move points accordingly

## Derivation of Gradient Descent.
        For example of the derivation i am going to use Mean Square Error (MSE).
$$
y \  is \ actual \\  
y^{pred} \ is \ model \ going \ to find \\ 
y^{pred} = wx + b \\
MSE = \frac{1}{n}\sum_{i = 0}^{n} (y - y^{pred})^{2}
$$

To reduce the cost function need to get the optmized value for w and b, To get the optmize value of y based on the x need to find the optmize the w and b.

$MSE = \frac{1}{n}\sum_{i = 0}^{n} (y - (wx + b))^{2}$

To calculate the gradient of w and b, need to calculate the chain rule.

Why chain rule? \
 w and b is in inner function.

Explain chain rule. 

To calculate the derivate of x. 1st calculate the derivate of outer function, Then calculate the derivative of inner function and multiply them.

calculate the derivative of x. 
$\displaystyle \frac{\partial }{\partial x} (f[g(x)])$


$\displaystyle \frac{\partial }{\partial x} (f[g(x)]) =  f^{'}[g(x)].g^{'}(x)$  

example 1. 
$$\displaystyle \frac{\partial }{\partial x} [5x + 3]^4 =  4[5x+3] ^ {3} . [5 + 0] \\ 
= 4[5x+3] ^ {3} . 5  \\
= 20 [5x + 3]^{3}
$$

example 2. 
$$\displaystyle \frac{\partial }{\partial x} {[x^{2} - 3x]}^{5} =  5[x^{2} - 3x]^{4} . [2x - 3] $$

Back to MSE

$$
MSE = \frac{1}{n}\sum_{i = 0}^{n} (y - (wx + b))^{2} \\
derivation \ of \ MSE=  \frac{1}{n}\sum_{i = 0}^{n} 2(y - (wx + b)) . (Partial \ derivation \ of \ w \ and \ b) -> eq 1 \\
$$
(Partial derivation of w and b) this part is going to replace by derivation of w and b   
Calculate the inner derivation of w and b  
To find two different derivation need to calculate partial derivation  

Partial derivation of w

$$\displaystyle \frac{\partial }{\partial w} (y - (wx + b)) =  -x $$

Combine with eq1
$$

=  \frac{1}{n}\sum_{i = 0}^{n} 2(y - (wx + b))\ . -x \\
=  \frac{1}{n}\sum_{i = 0}^{n} -2x(y - (wx + b))\  \\
$$
Above is final derivation of w 
\
\
Partial derivation of b

$$\displaystyle \frac{\partial }{\partial b} (y - (wx + b)) =  -1 $$
Combine with eq1
$$

=  \frac{1}{n}\sum_{i = 0}^{n} 2(y - (wx + b))\ . -1 \\
=  \frac{1}{n}\sum_{i = 0}^{n} -2(y - (wx + b))\ \\
$$
Above is final derivation of w   
In the final derivation 2 is small value so it can be negligible.

$$
\displaystyle \frac{\partial }{\partial w} =  - \frac{1}{n}\sum_{i = 0}^{n} x(y - (wx + b)) \\
 \\
\displaystyle \frac{\partial }{\partial w} =   - \frac{1}{n}\sum_{i = 0}^{n} (y - (wx + b))
$$

\- is moved to starting. This means subract from previous value in the code

```python
    #lr is the learning rate
    w -= lr * (-2 * X.dot(error).sum() / n)
    b -= lr * (-2 * error.sum() / n)
    # or
    w -= lr * (X.dot(error).sum() / n)
    b -= lr * (* error.sum() / n)
```
## Types of Gradient
 - Batch or Vanilla Gradient Descent \
        It calculate gradient using all the points. It uses more memory, it will be slow, but it gives more smoother curve

 - Sophisticated Gradient Descent \
        It calculate gradient using random one sample at a time. It uses less memory, it is fast, but it is not stable, It has high noise

 - Mini-Batch Gradient Descent
        It will split the dataset into the given amount of batches, and calculate the gradient for that group or subset of the dataset and update the weight, It will be between Vanilla Gradient Descent and Sophisticated Gradient Descent

## Hyperparameter tuning
 - Momentum \
        It will calculate exponentially weighted average of the gradient. It will eleminate the oscillation
 - Nesterov Accelerated Gradient
 - Decay rate
 - Adam
 - RMSprop
 - Regularization