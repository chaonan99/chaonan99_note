## Gated Siamese Convolutional Neural Network Architecture for Human Re-Identification

* Author: Rahul Rama Varior, NTU Singapore; Mrinal Haloi, Nanyang technological Universi; [Gang Wang](http://ihome.ust.hk/~gwang/)
* Picutre of the model

![2016_10_14_cebff7ce866e92a1c89e96dfc777d19](http://oa5omjl18.bkt.clouddn.com/2016_10_14_cebff7ce866e92a1c89e96dfc777d19.png "Add Description")

* Current state-of-the-art on [Market-1501](201609.md#market-1501).

### Contribution
1. Architecture of baseline siamese network for person re-id.
2. Matching gate between convolutional blocks.

### Matching gate (MG) structure
* Feature summarization
    * Aggregates the local feature along a horizontal stripe.
    * Deal with problem of changed view point (view point change in re-id typically in the horizontal direction, same parts are very likely to be along the same horizontal region).
    * Equation and dimention:
        ![equation](http://latex.codecogs.com/svg.latex?y_%7Br1%7D%3Df%28w%2Ax_%7Br1%7D%29); ![equation](http://latex.codecogs.com/svg.latex?y_%7Br2%7D%3Df%28w%2Ax_%7Br2%7D%29)
        where ![equation](http://latex.codecogs.com/svg.latex?x_%7Bri%7D%5Cin%20%5Cmathbb%7BR%7D%5E%7B1%5Ctimes%20c%5Ctimes%20h%7D) is the ![equation](http://latex.codecogs.com/svg.latex?r%5E%7Bth%7D) row of feature map. ![equation](http://latex.codecogs.com/svg.latex?w%5Cin%20%5Cmathbb%7BR%7D%5E%7B1%5Ctimes%20c%5Ctimes%20h%5Ctimes%20h%7D) (maybe ![equation](http://latex.codecogs.com/svg.latex?%5Cmathbb%7BR%7D%5E%7B1%5Ctimes%20c%5Ctimes%201%5Ctimes%20h%7D)) and ![equation](http://latex.codecogs.com/svg.latex?y_%7Br1%7D%5Cin%20%5Cmathbb%7BR%7D%5E%7B1%5Ctimes%201%5Ctimes%20h%7D) (maybe ![equation](http://latex.codecogs.com/svg.latex?%5Cmathbb%7BR%7D%5E%7B1%5Ctimes%201%5Ctimes%20h%5Ctimes%20h%7D)).
* Feature similarity
    * Euclidean distance of ![equation](http://latex.codecogs.com/svg.latex?y_%7Br1%7D) and ![equation](http://latex.codecogs.com/svg.latex?y_%7Br2%7D)
        ![equation](http://latex.codecogs.com/svg.latex?g_r%5Ei%3D%5Cexp%28%5Cfrac%7B-%28y_%7Br1%7D%5Ei-y_%7Br2%7D%5Ei%29%5E2%7D%7Bp_i%5E2%7D%29)
        where ![equation](http://latex.codecogs.com/svg.latex?g_r%20%5Cin%20%5Cmathbb%7BR%7D%5E%7B1%5Ctimes%201%5Ctimes%20h%7D)
    * ![equation](http://latex.codecogs.com/svg.latex?p_i) decides the variance of the Gaussian function, learnable, should set a higher initial value.
* Filtering and boosting the features
    * Repeat ![equation](http://latex.codecogs.com/svg.latex?g_r) c times horizontally to obtain ![equation](http://latex.codecogs.com/svg.latex?G_r%5Cin%20%5Cmathbb%7BR%7D%5E%7B1%5Ctimes%20c%5Ctimes%20h%7D).
    * Add filtered feature to original feature.
        ![equation](http://latex.codecogs.com/svg.latex?a_%7Br1%7D%5Ei%3Dx_%7Br1%7D%5Ei%2Bx_%7Br1%7D%5Ei%5Codot%20G_r%5Ei)
        ![equation](http://latex.codecogs.com/svg.latex?a_%7Br2%7D%5Ei%3Dx_%7Br2%7D%5Ei%2Bx_%7Br2%7D%5Ei%5Codot%20G_r%5Ei)
    * Perform L2 normalization across channels after this

### Result
* Dataset: Market-1501, CUHK-03, VIPeR.
* Baseline S-CNN outperform most CNN approaches. With MG gaining further improvement.
* Visualization of gate. Low gate activation means low similarity.
    ![2016_10_14_abc0a52873dfd63db5fbe8ad154b87c](http://oa5omjl18.bkt.clouddn.com/2016_10_14_abc0a52873dfd63db5fbe8ad154b87c.png "Add Description")
