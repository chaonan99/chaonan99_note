# NIPS 2016 Tutorial: Generative Adversarial Networks

* [paper](http://cn.arxiv.org/pdf/1701.00160v3.pdf)
* [slide](http://www.iangoodfellow.com/slides/2016-12-04-NIPS.pdf)

## Why studying Generative Modeling?
* Represent and manipulate high dimensional probability distribution
* Incorporated with reinforcement learning
    - A connection between generative adversarial networks, inverse reinforcement learning, and energy-based models. [paper](https://arxiv.org/abs/1611.03852)
* Can be trained with missing data, *semi-supervised leaning*
* Enable machine learning to work with multi-modal outputs
* Many tasks intrinsically require realistic generation of samples
    - Single image super-resolution. (Photo-realistic single image super-resolution using a generative adversarial network. [paper](https://arxiv.org/abs/1609.04802))
    - Create art.
    - Image to image translation.

## How does Generative Models Work?
### Maximum likelihood
* Maximum likelihood estimation: choose the parameters for the model that maximize the likelihood of the training data.
    - Origin: $\theta^* = \underset{\theta}{\arg\max}\prod_{i=1}^mp_{model}(x^{(i)}; \theta)$
    - Log: $\theta^* = \underset{\theta}{\arg\max}\sum_{i=1}^m\log p_{model}(x^{(i)}; \theta)$
    - KL divergence: $\theta^* = \underset{\theta}{\arg\min}D_{KL}(p_{data}(x)\|p_{model}(x; \theta))$

### Deep generative models
* A taxonomy of deep generative models
    * ![taxonomy](http://img.blog.csdn.net/20170204161459406?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

#### **Explicit density models**: directly define $p_{model}(x;\theta)$
*  **Tractable explicit models**: careful construction of models whose structure guarantees their tractability.
    * **Fully visible belief networks (FVBN)**
        * Use chain rule of probability to decompose n-D distribution to 1-D
        * $$p_{model}(x) = \prod_{i=1}^np_{model}(x_i|x_1,\dots,x_{i-1})$$
        * One of the three most popular
        * Basis of WaveNet
        * Cannot be parallelized, too slow
    * **Nonlinear independent components analysis **
        * Defining continuous, nonlinear transformations between two different spaces
        * $$p_x(x) = p_z(g^{−1}(x))|\det(\frac{\partial g^{−1}(x)}{
\partial x})|$$
        * Latent variable $z$ should have the same dimension as $x$.
* **Explicit models requiring approximation**: using intractable density function and use approximations to maximize the likelihood.
    * **Variational approximations**
        * Defines a lower bound
        * $L(x;\theta) \leq \log p_{model}(x;\theta).$
        * A learning algorithm that maximizes L is guaranteed to obtain at least as high a value of the log-likelihood as it does of $L$.
        * Variational autoencoder
    * **Markov chain approximations**
        * $x' ∼ q(x'| x)$.
        * By repeatedly updating $x$ according to the transition operator $q$, Markov chain methods can sometimes guarantee that x will eventually converge to a sample from $p_{model}(x)$.
        * Convergence can be very slow
        * Boltzmann machines

#### **Implicit density models**: only sample for $p_{model}(x;\theta)$
* GAN is almost the only
* Compare GAN with others
    * Can generate samples in parallel
    * The design of generator function has very few restrictions
    * No Markov chains are needed
    * No variational bound is needed
    * Subjectively better

## How do GANs work?
### Framework
* ![gan framework](http://img.blog.csdn.net/20170204181502201?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* Generator and discriminator
* Generator create samples intended to come from the same distribution as the training data.
* Discriminator examines samples to determine whether they are real or fake.
* Generator function: $x = G(z; \theta^{(G)})$, discriminator function: $D(x; \theta^{(D)})$. Both are differentiable wrt input ($z$ or $x$) and parameter ($\theta^{(G)}$ or $\theta^{(D)}$).
* Generator function $G(z)$ input $z$ can be provided at any layer and do not need to be the same dimension with $x$.

### Training
* Cost function for discriminator
    * $$J^{(D)}(\theta^{(D)}, \theta^{(G)})=-\frac12 \mathbb{E}_{x\sim p_{data}}\log D(x) -\\ \frac12 \mathbb{E}_z\log(1 - D(G(z)))$$
    * Cross entropy, training sample from both real data and generator.
* GANs make approximations based on using supervised learning to estimate a ratio of two densities: $\frac{p_{data}(x)}{p_{model}(x)}$
