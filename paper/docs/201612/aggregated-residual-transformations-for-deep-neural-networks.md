## Aggregated Residual Transformations for Deep Neural Networks
* [paper](http://cn.arxiv.org/pdf/1611.05431v1)
* Author: [Saining Xie](http://vcl.ucsd.edu/~sxie/about/), [Ross Girshick](https://people.eecs.berkeley.edu/~rbg/), Piotr Dollar´, [Zhuowen Tu](http://pages.ucsd.edu/~ztu/), [Kaiming He](http://kaiminghe.com/)

### Model
* Solution space of Inception architecture is a strict subspace of the solution space of a single large layer (e.g., 5×5) operating on a high-dimensional embedding.
* The transformations to be aggregated are all of the same topology.
* Equivalent forms:
    ![equivalent](http://img.blog.csdn.net/20161215130302222?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* This strategy exposes a new dimension, which we call “cardinality” (the size of the set of transformations), as an essential factor in addition to the dimensions of depth and width.

### Experiemnt
* See original paper for training details.
* Increasing cardinality is more efficient than increasing depth/width.
* ImageNet
    * 224x224: 20.4% top-1, 5.3% top-5
    * 320x320/crop-to-299x299: 19.1% top-1, 4.4 top-5
* ImageNet 5K (5000 class)
* CIFAR
    * -10 3.58%
    * -100 17.31%
* COCO detection
    * 51.9 AP@0.5
    * 30.0 AP