## Xception: Deep Learning with Depthwise Separable Convolutions
* [paper](http://cn.arxiv.org/pdf/1610.02357v2)

### Intuition
* Inception series
* Conv maps cross-channel correlation and spatial correlation at the same time.
* Inception module makes this process easier and more efficient by explicitly factoring it into a series of operations that would independently look at cross-channel correlations and at spatial correlations.
* 1x1 Conv -> cross-channel correlation; 3x3 & 5x5 Conv -> spatial correlation.
    ![Inception](http://img.blog.csdn.net/20161213145839016?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* An extreme version of this separation is to entirely decouple the cross-channel and spatial operations, naming **Xception**.

### Xception
* Xception module:
    ![Xception](http://img.blog.csdn.net/20161213145912704?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* First use 1x1 Conv
* Conduct depthwise separable convolution (DSC): each feature-map have different 3x3 Conv, then concatenate the result of each Conv.
* Advantages: Efficient parameter usage
* Whole model
    ![Model](http://img.blog.csdn.net/20161213145936293?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

### Experiment
* Dataset: JET (internal Google dataset), ImageNet, FastEval14k.
* Result
    * Xception converges faster than Inception V3 and gets higher accuracy.
    * 21.0% top-1, 5.5% top-5 error on ImageNet.
    * Better with residual connection.
    * Worse with non-linear in between the 1x1 and DSC.