# Bayes Decision Theory
19th, Sept.

Reference: [Corso's lecture at Buffalo](https://www.cse.buffalo.edu/~jcorso/t/CSE555/files/lecture_bayesiandecision.pdf)

## Assumptions
* Decision problem is posed in probabilistic terms
* All relevant probability values are known

## Priori and posterior
* Define a (probabilistic) variable ![equation](http://latex.codecogs.com/svg.latex?%5Comega) ranging from ![equation](http://latex.codecogs.com/svg.latex?%5Comega_i%2C%20i%3D1%2C%5Cdots%2Cc),
![equation](http://latex.codecogs.com/svg.latex?%5Csum_%7Bi%3D1%7D%5EcP%28%5Comega%3D%5Comega_i%29%3D1)

* The a priori or prior probability reflects our knowledge of how likely we expect a certain state of nature before we can actually observe said state of nature.
![equation](http://latex.codecogs.com/svg.latex?P%28%5Comega%3D%5Comega_i%29)

* A **feature** is an observable variable, scalar ![equation](http://latex.codecogs.com/svg.latex?x) or vector ![equation](http://latex.codecogs.com/svg.latex?%5Cmathbf%7Bx%7D)

* Likelihood (Class-Conditional Density): the probability density function for feature, given that the state of nature is ![equation](http://latex.codecogs.com/svg.latex?%5Comega)
![equation](http://latex.codecogs.com/svg.latex?p%28%5Cmathbf%7Bx%7D%7C%5Comega%29)

> Note that lower-case p refers to  probability density function and upper-case P refers to probability.

* Posterior probability: the probability of a certain state of nature
given our observables
![equation](http://latex.codecogs.com/svg.latex?P%28%5Comega%2C%20%5Cmathbf%7Bx%7D%29%20%3D%20P%28%5Comega%7C%5Cmathbf%7Bx%7D%29p%28%5Cmathbf%7Bx%7D%29%20%3D%20p%28%5Cmathbf%7Bx%7D%7C%5Comega%29P%28%5Comega%29)
![equation](http://latex.codecogs.com/svg.latex?P%28%5Comega%7C%5Cmathbf%7Bx%7D%29%3D%5Cfrac%7BP%28%5Comega%2C%20%5Cmathbf%7Bx%7D%29%7D%7Bp%28%5Cmathbf%7Bx%7D%29%7D%3D%5Cfrac%7Bp%28%5Cmathbf%7Bx%7D%7C%5Comega%29P%28%5Comega%29%7D%7B%5Csum_ip%28%5Cmathbf%7Bx%7D%7C%5Comega_i%29P%28%5Comega_i%29%7D)

* Use Bayes Formula to make decision.

## Probability of error
* Decision governed by posterior
![equation](http://latex.codecogs.com/svg.latex?%5Comega%5E%2A%3D%5Carg%5Cmax_iP%28%5Comega_i%7C%5Cmathbf%7Bx%7D%29)
* Probability of error
![2016_09_19_c585278e78e9a334af8b5126f41f413d](http://oa5omjl18.bkt.clouddn.com/2016_09_19_c585278e78e9a334af8b5126f41f413d.png "Add Description")

* Minimize average probability of error
![equation](http://latex.codecogs.com/svg.latex?%5Cmin%20P%28error%29%3D%5Cint_%7B-%5Cinfty%7D%5E%7B%2B%5Cinfty%7DP%28error%7C%5Cmathbf%7Bx%7D%29P%28%5Cmathbf%7Bx%7D%29d%5Cmathbf%7Bx%7D)

* **Decision making relies on both the priors and the likelihoods and Bayes Decision Rule combines them to achieve the minimum probability of error**