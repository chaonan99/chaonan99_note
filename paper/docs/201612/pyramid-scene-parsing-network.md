## Pyramid Scene Parsing Network
* [paper](https://arxiv.org/pdf/1612.01105.pdf)
* [project page](http://appsrv.cse.cuhk.edu.hk/~hszhao/projects/pspnet/index.html)
* [code](https://github.com/hszhao/PSPNet)
* 1-st place on ImageNet scene parsing challenge 2016

### Parsing overview
* Datasets
    * [LMO](http://people.csail.mit.edu/celiu/LabelTransfer/code.html)
    * [PASCAL VOC](http://host.robots.ox.ac.uk/pascal/VOC/)
    * [ADE20K dataset](http://groups.csail.mit.edu/vision/datasets/ADE20K/)
    * [Cityscapes](https://www.cityscapes-dataset.com/)
* FCN is the baseline model for deep learning based parsing
    * Research line 1: multi-scale feature ensembling
    * Research line 2: structure prediction
    * FCN has also been used in depth estimation, image restoration, image super-resolution.
* Some prior works use global image-level information for scene understanding

### Intuition
* FCN method suffers from mismatched relationship, confusion categories and inconspicuous classes
* Global average pooling fuses different stuff in a single vector and may lose the spatial relation. Global context information along with sub-region context may be more helpful.

### Model

![Model](http://appsrv.cse.cuhk.edu.hk/~hszhao/projects/pspnet/figures/pspnet.png)

* Pyramid pooling: bin size of 1x1, 2x2, 3x3, 6x6, both max and average pooling
* Auxiliary loss in ResNet-101

### Experiment
* Datasets: ImageNet scene parsing (ADE20K), PASCAL VOC 2012, Cityscapes
* Settings: poly learning rate, augmentation, momentum = 0.9 and weight decay = 0.0001.
* Large cropsize can get good performance (consistant with our experiment in ResNet)
* Batch size in batch normalization layer is important.
* Ablation study of settings
    * Average pooling is better than max
    * Pyramid is better than global pooling
    * Dimension reduction after pooling and concatenate is helpful
* Ablation study of auxiliary loss
    * `\alpha = 0.4` yields best performance
* Ablation study for ResNet depth
    * The deep the better
    * All ResNet is pre-trained on ImageNet
* Experiment on PASCAL VOC 2012
    * 10,582, 1,449 and 1,456 images for training, validation and testing
    * Top accuracy on all classes w/o MS COCO pre-training, top on most classes w/ MS COCO pre-training.
    * 85.4% mIoU.
* Cityscapes
    * 2,975, 500, and 1,525 for training, validation and testing, 19 categories containing both stuff and objects.
    * 20,000 coarsely annotated images, can be used for training.
    * Out-performs other methods with notable advantage (See project page for statistics)

