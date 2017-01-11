## Network in Network
[paper link](http://arxiv.org/pdf/1312.4400v3.pdf)

![2016_09_01_242a128ecc742b42995196a59e6d5a4](http://oa5omjl18.bkt.clouddn.com/2016_09_01_242a128ecc742b42995196a59e6d5a4.png "Network in network, MLP")

### Highlights

1. Propose a model replacing conventional convolution operation with **multilayer perceptron (MLP)**, to gain better abstraction for all levels of features.
    * The cross channel parametric pooling layer is  is equivalent to 1x1 convolution layer with 1x1 kernel.
2. Replacing fully connected (+dropout) with **global average pooling (GAP)**.
    * Generate one feature map for each corresponding category of the classification task in the last mlpconv layer.
    * More native to the convolution structure (enforcing correspondence between feature maps and categories).
    * No parameter, avoid overfitting.

### Multilayer perceptron (MLP)

Traditional convolutional layer:

![equation](http://latex.codecogs.com/svg.latex?f_%7Bi%2Cj%2Ck%7D%3D%5Cmax%28w_k%5E%5Cmathbf%7BT%7Dx_%7Bi%2Cj%7D%2C0%29)

Here ![equation](http://latex.codecogs.com/svg.latex?%28i%2Cj%29) is the pixel in the feature map, ![equation](http://latex.codecogs.com/svg.latex?x_%7Bi%2Cj%7D) stands for the input patch centered at location ![equation](http://latex.codecogs.com/svg.latex?%28i%2Cj%29), and ![equation](http://latex.codecogs.com/svg.latex?k) is used to index the channels of the feature map.

mlpconv:

![equation](http://latex.codecogs.com/svg.latex?f_%7Bi%2Cj%2Ck_1%7D%5E1%3D%5Cmax%28%7Bw_%7Bk_1%7D%5E1%7D%5E%5Cmathbf%7BT%7Dx_%7Bi%2Cj%7D%2Bb_%7Bk_1%7D%2C0%29)

![equation](http://latex.codecogs.com/svg.latex?...)

![equation](http://latex.codecogs.com/svg.latex?f_%7Bi%2Cj%2Ck_n%7D%5En%3D%5Cmax%28%7Bw_%7Bk_n%7D%5En%7D%5E%5Cmathbf%7BT%7Df_%7Bi%2Cj%7D%5E%7Bn-1%7D%2Bb_%7Bk_n%7D%2C0%29)

![equation](http://latex.codecogs.com/svg.latex?n) is the number of layers in the multilayer perceptron.

### Result

1. State-of-the-art on CIFAR-10.
2. No evidance to show that mlp really performs better than conventional convolution. Seems that the paper made no direct comparison on direct connect with dropout in every layer. So one can argue that the performance improvement is gained by using dropout in every layer.
3. To a small linear network, classification result on CIFAR-10 is worse with GAP than with fully connect + dropout.