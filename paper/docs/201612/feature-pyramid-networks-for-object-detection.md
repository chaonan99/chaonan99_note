## Feature Pyramid Networks for Object Detection
* [paper](http://arxiv.org/pdf/1612.03144v1)

### Intuition
* Multi-scale is important in traditional methods
* Current detection system use single shot CNN to save time and memory (Faster R-CNN)
* CNN is capable of representing higher-level semantics, but not all levels are semantically strong
* Single Shot Detector (SSD) is one of the first attempts at using ConvNet's pyramidal feature, but they add new layers after high up layer, which may lose information in high-resolution feature map
* Main contribution: perform multi-scale in the network

### Model
* Feature Pyramid Network (FPN) building block
    * ![FPN block](http://img.blog.csdn.net/20161227164614908?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
    * The feature maps in the picture above are from the last layer of each **stage** in ConvNet
    * Nearest neighbor upsampling
    * Denotes final set of feature maps as $\{P_2, P_3, P_4, P_5\}$, corresponding to $\{C_2, C_3, C_4, C_5\}$
* FPN in Region Proposal Network (RPN)
    * Replacing single-scale feature map with FPN
    * Anchors with different aspect ratios: 1:2, 1:1, 2:1
    * 15 anchors over the pyramid
* FPN in Fast R-CNN

### Experiment
* Evaluate on COCO `minival` set
* Surpass 2016 COCO winner
* Lateral and top-down connection is helpful