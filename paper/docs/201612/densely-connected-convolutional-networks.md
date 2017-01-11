## Densely Connected Convolutional Networks
* [Code](https://github.com/liuzhuang13/DenseNet)
* [paper](http://cn.arxiv.org/pdf/1608.06993v3)
* A dense block with 5 layers and growth rate 4:
![illustration](https://cloud.githubusercontent.com/assets/8370623/17981494/f838717a-6ad1-11e6-9391-f0906c80bc1d.jpg)

### Intuition
* Current trend of CNN architecture: create short paths from early layers to later layers.
    * ResNet
    * Highway network: The first network with more than 100 layers, bypassing paths
    * Stochastic depth: Improves the training of deep residual networks by dropping layers randomly during training, which manages to train a 1202-layer ResNet
    * FractalNets
* Wide filter is helpful.
* Connect all layers with each other.
* Combine features by concatenating them (ResNet combines by summation).
* DenseNet layers are very narrow (12 feature-maps per layer), resulting in less parameters

### Model
![dense block](https://cloud.githubusercontent.com/assets/8370623/17981496/fa648b32-6ad1-11e6-9625-02fdd72fdcd3.jpg)

* Dense connectivity: concatenate all the preceding layers:
    ![equation](http://latex.codecogs.com/svg.latex?x_l%20%3D%20H_l%28%5Bx_0%2C%20x_1%2C%20%5Cdots%2C%20x_%7Bl-1%7D%5D%29)
* Composite function:
    `H_l` is defined as `BN + ReLU + 3x3 Conv`
* Pooling and dense block
    * See figure above
    * **Transition layer** between dense blocks, consist of `BN + 1x1 Conv + 2x2 AveragePooing`
* Growth rate `k`:
    * The number of output feature-maps.
    * The `l`-th layer will have `k x (l-1) + k_0` input feature-maps (`k_0`:input image channels)
* Bottleneck layers
    * Introduce 1x1 Conv before 3x3 Conv to reduce number of feature-maps will improve computation efficiency.
    * `H_l` is changed to `BN + ReLU + 1x1 Conv + BN + ReLU + 3x3 Conv`
    * `1x1 Conv` reduce the input to `4k` feature-maps in the experiment.
* Compression
    * Reduce feature-maps number in transition layer by factor ![equation](http://latex.codecogs.com/svg.latex?%5Ctheta)

### Experiment
* Datasets
    * CIFAR-10/100, 32x32
        * Zero-padded with 4 pixels on each side
        * Randomly cropped to again produce 32×32 images
        * Half of the images are then horizontally mirrored
    * SVHN (Street View House Numbers), 32x32
    * ImageNet, 224x224, 1.2m for training, 50000 for validation, 1000 classes
* Settings: weight decay 10e-4, Nesterov momentum of 0.9 w\o dampening, learning rate 0.1 with decay scheme, dropout when no data augmentation
* Accuracy result:
    * 3.46% on CIFAR-10, L=190, k=40
    * 17.18% on CIFAR-100, L=190, k=40
    * 1.59% on SVHN, L=100, k=24
* Capacity: the performance continues improving when L, k increase, showing the DenseNet is less prone to overfitting (???)
* Parameter efficiency.

### Comment
* By [Xiangyu Zhang](https://scholar.google.com/citations?user=yuB-cfoAAAAJ&hl=en).
* The reason that DenseNet would work is very likely to be the Pyramidal design (i.e. increasing number of filters along the network flow). Dense connection may not be superior according to his previous experiment. Other papers has demonstrate the effect of Pyramidal design, like Deep Pyramidal Residual Networks, which brings about an obvious 1~2% decrease in error rate on CIFAR.