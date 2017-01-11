## FlowNet: Learning Optical Flow with Convolutional Networks

* [paper](http://arxiv.org/pdf/1504.06852v2)
* [code](https://github.com/liruoteng/FlowNet)

### Highlight
* First paper to use trained CNN for optical flow estimation
* Introduce novel correlation layer
* Refine network by upsampling

### Model
* ![model](http://img.blog.csdn.net/20170111131233072?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* FlowNetSimple: concatenate two consecutive images.
* FlowNetCorr: use correlation layer
* Correlation layer
    * Calculated between two feature maps
    * $c(x_1, x_2) = \sum_{o \in [-k, k]\times [-k, k]}<f_1(x_1+o), f_2(x_2+o)>$
    * See model picture for an illustration
* Refinement
    * ![refine](http://img.blog.csdn.net/20170111131802783?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
    * Concatenate the upsampled flow prediction and conv feature map

### Experiment
* Datasets:
    * Middlebury
    * KITTI
    * Sintel
    * Flying Chairs (proposed, auto generated)
* Loss function: endpoint error -- Euclidean distance between the predicted flow vector and GT.
* Conclusion
    * FlowNet performs a little worse than other OF algorithm, but obviously faster.
    * Network trained on Flying Chairs (auto generated) data has good generalization ability on natural scenes.
