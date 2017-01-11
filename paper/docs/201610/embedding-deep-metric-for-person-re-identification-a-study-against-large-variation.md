## Embedding Deep Metric for Person Re-identification: A Study Against Large Variation
* ECCV 2016
* Author: [Hailin Shi](http://www.cbsr.ia.ac.cn/users/hailinshi/), Yang Yang, Xiangyu Zhu, Shengcai Liao, Zhen Lei, Weishi Zheng, [Stan Z. Li](http://www.cbsr.ia.ac.cn/users/szli/)

### Overview
* Re-id research topics:
    * Improving discriminative features.
    * Good metric for comparison.
    * This paper mainly focus on learning good metrics.
* Influenced by face recognition method (the author also works on face recognition).
* Contributions:
    * **Moderate Positive Mining**, a novel positive sample selection strategy for training CNN while the data has large intra-class variations.
    * **Metric weight constraint** (combine Euclidean distance with Mahalanobis distance).

### Moderate positive mining
* Intuitions
    * Positive samples with large distance is harmful.
    * Positive samples with too little distance have little contribution to convergance.
    * What to do: reduce the intra-class variance while preserving the intrinsic graphical structure of pedestrian data via mining the moderate positive pairs in the local range (picture).
    ![<picture here>](http://img.blog.csdn.net/20161025124254314)
* Algorithm of choosing moderate positive sample (picture)
    * Compute the distances of 1-all positive&negative samples
    * Mine the hardest negative sample (min distance negative), ![equation](http://latex.codecogs.com/svg.latex?distance%20%3D%20d%5E%2A)
    * Subset of positive samples where distance is larger than ![equation](http://latex.codecogs.com/svg.latex?d%5E%2A)
    * In this subset, find positive pair with min distance -- moderate positive
    ![<picture here>](http://img.blog.csdn.net/20161025124317408)

### Metric weight constraint
* Euclidean distance shortcomings:
    * Sensitive to the scale?
    * Blind to the correlation across dimensions
    * Using the Mahalanobis distance is a better choice for multivariate metric, argued by other work
* Another FC after distance between features is calculated to gain Mahalanobis distance.
    * Get Mahalanobis distance
        * ![equation](http://latex.codecogs.com/svg.latex?d%28x_1%2C%20x_2%29%3D%5Csqrt%7B%28x_1-x_2%29%5E%5Cmathbf%7BT%7DM%28x_1-x_2%29%7D)
        * ![equation](http://latex.codecogs.com/svg.latex?M%3DWW%5E%5Cmathbf%7BT%7D) (ensure ![equation](http://latex.codecogs.com/svg.latex?M) is semi-definate matrix)
        * ![equation](http://latex.codecogs.com/svg.latex?d%28x_1%2C%20x_2%29%3D%7C%7CW%5E%5Cmathbf%7BT%7D%28x_1-x_2%29%7C%7C_2)
    * This can be implemented by an FC layer
        ![equation](http://latex.codecogs.com/svg.latex?y%3Df%28W%5E%5Cmathbf%7BT%7Dx%29)
* Weight constraint
    * Euclidean better generalization ability, less discriminability.
    * Balance between Euclidean and Mahalanobis distance.
    * ![equation](http://latex.codecogs.com/svg.latex?M) should have large values at the diagonal (Euclidean) and small values elsewhere, by giving constraint:
        * ![equation](http://latex.codecogs.com/svg.latex?%7C%7CWW%5E%5Cmathbf%7BT%7D-I%7C%7C%5E2_F%5Cleq%20C)
    * Further combine the constraint into the loss function as a regularization term:
        * Triplet loss: ![equation](http://latex.codecogs.com/svg.latex?L%20%3D%20d%28x_1%2C%20x_2%5Ep%29%2B%5Bm-d%28x_1%2C%20x_2%5En%29%5D) (margin set to 2 in the experiment)
        * Regularization: ![equation](http://latex.codecogs.com/svg.latex?%5Chat%7BL%7D%3DL%2B%5Cfrac%5Clambda2%7C%7CWW%5E%5Cmathbf%7BT%7D-I%7C%7C%5E2_F) (tune ![equation](http://latex.codecogs.com/svg.latex?%5Clambda) to get the best trade-off)
        * Gradient w.r.t ![equation](http://latex.codecogs.com/svg.latex?W) is computed by ![equation](http://latex.codecogs.com/svg.latex?%5Cfrac%7B%5Cpartial%20%5Chat%7BL%7D%7D%7B%5Cpartial%20W%7D%3D%5Cfrac%7B%5Cpartial%20L%7D%7B%5Cpartial%20W%7D%2B%5Clambda%28WW%5E%5Cmathbf%7BT%7D-I%29W)

### CNN architecture
![<picture here>](http://img.blog.csdn.net/20161025124349065)

![CNN structure](http://img.blog.csdn.net/20161025124443754)

* 3 branches CNN
    * Original image 128x64 => 3x64x64 (with overlap)
    * Untied (unshared) filter between CNN branches to learn specific features from the different human body parts of pedestrian image.

### Experiments
* Their baseline is very weak (worse than CUHK-03 baseline)
* Three parts are analyzed
    * Moderate positive and hard negative (improve 10%+)
    * Weight constraint, tune on ![equation](http://latex.codecogs.com/svg.latex?%5Clambda) (![equation](http://latex.codecogs.com/svg.latex?%5Clambda) around ![equation](http://latex.codecogs.com/svg.latex?10%5E%7B-2%7D) gets good trade-off)
    * Tied or untied filters between branches (Untied a little better)
* Augmentation
    * Random translation
    * Randomly cropped (0-5 pixels) in horizon and vertical, and stretched to recover the size
* Datasets
    * CUHK03 (Rank-1: 61.32% with hand-crafted bbox, 52.09% with detected bbox)
    * CUHK01 + Market-1501 in training (Rank-1: 86.59%)
    * VIPeR (Rank-1: 43.39%)