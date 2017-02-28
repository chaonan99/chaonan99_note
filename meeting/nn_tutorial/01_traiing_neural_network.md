# Training Neural Network

## Machine Learing as Optimization
* Supervised learning
    * $\min_\theta d(y,\hat{y})$
* Regularized sypervised learning
    * $\min_\theta d(y,\hat{y}) + r(\hat{y})$
* Probabilistic interpretation
    * $\log p(y|\hat{y})$
* Gradient descent
    $\theta_{t+\lambda} = \theta_{t} - \frac{}{}$
* Dissretized, gradient descent may not converge
* Theoratically can be solved by Newton's method ($H^{-1}$)
* Gauss-Newton algorithm
    * $X_{t+1}=X_t - \frac{\e f(X)}{\e X}$

## Linear Regression
* Gauss, $y=\hat{y}-WX$
* Too much channel, bottle neck use identity

## Backpropagation
* 

## CNN
* Convolution is linear
    * Equivalent to matrix multiply
    * Possion matrix
* Why not FC
    * Data is never enough
    * Translation invariance
    * Global minimum cannot be realized
* Convolution as matrix product
    * feature map $<N, C, H', W'>$
    * weights $<K, C, H, W>$
    * K: for efficience
    * Steps
        * Image to column
        * Kernel to matrix
        * Matrix mul matrix
* Locally-connected
* Channl-wise convolution

## Nonlinearity
* Tanh: need exp (not recommended)
* Maxout
