## Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks
* [Paper](https://arxiv.org/pdf/1506.01497v3.pdf)
* Author: Shaoqing Ren, Kaiming He, Ross Girshick, and Jian Sun

### Overview
* Components of object detection system
    * Object proposals
        * Using Region Proposal Networks (RPN)
    * Deep network for classification
        * R-CNN mainly plays as a classifier, and it does not predict object bounds (except for refining by bounding box regression)
* Faster R-CNN combine RPN and object detection network (share computation)

### Faster R-CNN Architecture
#### RPN
* RPN of FRCNN
    ![Faster R-CNN](http://img.blog.csdn.net/20161120174146474)
* Use dCNN (Visualizing, VGG-16) to get feature map
* Sliding windows with size `n * n`(`n = 3`)
* Anchor is centered at the sliding window in question, and is associated with a scale and aspect ratio. `k = 9` anchors for each sliding window
#### Loss function
* Positive label for two kinds of anchors
    *  The anchor/anchors with the highest Intersection-overUnion (IoU) overlap with a ground-truth box
    * An anchor that has an IoU overlap higher than 0.7 with any ground-truth box.
* Negative label
    * An anchor that has an IoU ratio lower than 0.3 for all ground-truth boxes.
* Other anchors do not contribute to the training objective.
* Multi-task loss function
    $$L({p_i}, {t_i}) = \frac{1}{N_{cls}}\sum_iL_{cls} (p_i, p^∗_i)+\lambda\frac{1}{N_{reg}}\sum_ip^∗_i L_{reg} (t_i, t^∗_i).$$
    * $p_i$ probability of an ancor being an object.
    * $p^*_i$ ground truth (1->object, 0->non-object).
    * $L_{cls}$ classification loss (cross entropy).
    * $t_i$ vector representing the 4 parameterized coordinates of the predicted bounding box.
    * $t^*_i$ ground-truth box associated with a positive anchor.
    * $L_{reg} (t_i, t^∗_i) = R(t_i - t^∗_i)$, $R$ being the robust loss function ([smooth $L_1$](https://arxiv.org/abs/1504.08083)).
* Settings
    * $N_{cls}$ normalize classification loss by mini-batch size (256)
    * $N_{reg}$ normalize *reg* term by the number of anchor locations (about 2400)
    * $\lambda$ balancing parameter (10)
* Regression parameterizations method
    ![regression equation](http://img.blog.csdn.net/20161120180915799)
    * Note that the set of `k` anchors do not share weights as regressor in the formula.

#### Shared RPN and Fast R-CNN training
1. *Alternating training*: RPN <-> Fast R-CNN iterated.
    1. Train RPN with ImageNet pre-trained
    2. Train a separate FRCNN detector using the bbox in the first step
    3. Use detector network to initialize RPN training, shared conv layers fixed, only finetune RPN unique layers
    4. Keep the shared network fixed, only finetune the FRCNN unique layers
2. *Approximate joint training*: RPN and FRCNN forward sequentially, backward combine their loss functions.
    * Produces close results while reduces the training time by about 25-50% comparing with *Alternating*
3. *Non-approximate joint training*
    * FRCNN uses bounding box as input, but the *Approximate joint training* solution ignore the gradient w.r.t bounding box.
    * Need a differentiable RoI pooling layer w.r.t. bounding box coordinates -- **RoI warping** layer

### Experiments
* To reduce redundancy, we adopt non-maximum suppression (NMS) on the proposal regions based on their *cls* scores
* TODO ...
* Pre-region classifier
    * GoogleNet is better than VGG-16
    * 3fc classifier is better than 1fc classifier
    * Stride