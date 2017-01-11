## RefineNet: Multi-Path Refinement Networks for High-Resolution Semantic Segmentation
* [paper](http://arxiv.org/pdf/1611.06612v3.pdf)
* [code](https://github.com/guosheng/refinenet)

### Intuition
* Conv and pooling result in the lost of finer image structure, producing low resolution segmentation.
    * DeepLab solve this by  atrous (or dilated) convolutions to account for larger receptive fields without downscaling the image.
    * FCN and Hypercolumns exploits features from intermediate layers for generating high-resolution prediction.
* Feature from all levels help to generate semantic segmentation.

### Model
* Compare with standard CNN and Dilated convolutions
    ![compare](http://img.blog.csdn.net/20161223103630473?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* Single RefineNet structure
    ![RefineNet](http://img.blog.csdn.net/20161223103656829?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* Purpose of different components in RefineNet
    * RCU: finetune feature map for fusion task
    * Multi-resolution fusion: scale to the same resolution and sum
    * Chained residual pooling: capture background context from a large image region
    * Output convolutions: another RCU. There are 3 RCU between two RefineNet blocks (2 path). The whole net also adds 2 RCU before dense softmax classifier.
* Residual connection: in RefineNet unit and **between RefineNet blocks**

### Experiment
* Datasets
    * **Person-Part** 1717 training and 1818 testing, human parsing
    * **NYUDv2** 795 training, 654 testing, RGB-D images showing interior scenes
    * **PASCAL VOC 2012** training/validation/test -- 1464/1449/1456 (usually trained with MS COCO dataset)
    * **Cityscapes** training/validation** 2975/500, 19 classes
    * **PASCAL-Context** segmentation labels of the whole scene for PASCAL VOC images
    * **SUN-RGBD** around 10,000 RGB-D indoor images, 37 classes
    * **ADE20K MIT** 150 classes, more than 20K scene images
* Measurement: IoU, pixel accuracy, mean accuracy
* Augmentation: random scaling, random cropping and horizontal flipping
* The result on PASCAL VOC 2012 is not better than [PSPNet](https://arxiv.org/pdf/1612.01105.pdf) (see the following paper note)
* Variant of model
    * ![variant](http://img.blog.csdn.net/20161223132208376?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
    * 4-cascaded performs best but need more time