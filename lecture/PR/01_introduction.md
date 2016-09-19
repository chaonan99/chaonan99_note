# Introduction
12th, Sept.

## Contents of this lecture
* Concepts
* Math formulation
* System construction
* Theory and method
* Typical algorithm
* Newest problem

## Introduction
* observation -> decision
* Pattern: a physical arrangement of elements
* Recognition: an awareness that something perceived has been perceived before
* Sample, class, features. Classify samples according to their features
* System: object/pattern -> sensor -> feature extractor -> classifier -> decision/action
* Methods:
	+ Knowledge-based: AI, expert systems; syntax PR or structural PR
	+ **Data-based: statistical PR; ANN, SVM** (This lecture)
	+ Hybrid methods
* Classifier, decision boundary

## Eg: coin classification
* No observation, decided between two classes
	+ According to prior probabilities, choose bigger one
	+ Minimize error rate
* Have weight information
	+ According to posterior probabilities
	+ How to calculate posterior probabilities? Bias equation (below)
	+ Risk of the decision

![equation](http://latex.codecogs.com/svg.latex?P%28%5Comega_i%7Cx%29%3D%5Cfrac%7Bp%28x%2C%5Comega_i%29%7D%7Bp%28x%29%7D%3D%5Cfrac%7Bp%28x%7C%5Comega_i%29P%28%5Comega_i%29%7D%7Bp%28x%29%7D)

## Eg: How to do speech recognition
* Consider all possible text, extract feature, calculate posterior probabilities and do classification.
* Corpus
* MFCC feature for speech