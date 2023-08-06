# Optimizers
        Optimizers are used to reduce the error rate or cost function of a model by updating the weight

# Gradient Descent

    ## What is Gradient Descent?

    ## Why it is used in Deep learning?

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
\ \ \ \ \ \ \ \ \ \ \ \ \ = 4[5x+3] ^ {3} . 5  \\
\ \ \ \ \ \ \ \ \ \ \ \ = 20 [5x + 3]^{3}
$$

example 2. 
$$\displaystyle \frac{\partial }{\partial x} {[x^{2} - 3x]}^{5} =  5[x^{2} - 3x]^{4} . [2x - 3] $$

Back to MSE

$$
MSE = \frac{1}{n}\sum_{i = 0}^{n} (y - (wx + b))^{2} \\
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ derivation \ of \ MSE=  \frac{1}{n}\sum_{i = 0}^{n} 2(y - (wx + b)) . (Partial \ derivation \ of \ w \ and \ b) -> eq 1 \\
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
