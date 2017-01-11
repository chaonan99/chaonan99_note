## PVANET: Deep but Lightweight Neural Networks for Real-time Object Detection
* [paper](http://cn.arxiv.org/pdf/1608.08021v3)
* Author: Kye-Hyeon Kim, Sanghoon Hong, Byungseok Roh, Yeongjae Cheon, and Minje Park
* Intel Imaging and Camera Technology

### Highlight
* Speed up (real-time) detection process with a more efficient feature extraction CNN, without lossing too much accuracy.
* This network is smaller and more efficient than ResNet and can be a substitution of the latter.

### Main structure
* C.ReLU: Concatenated ReLU in early stage of CNN to reduce the number of computation.
    * In early stages, output nodes tend to be paired, i.e. one node's activation is the opposite of another's.
    * C.ReLU reduce the output channels by half and concatenate with negation.
* Inception
    * Not yet been widely applied.
    * Cost-efficient building block for multi-scale representation.
    * 1x1 Conv can preserve the receptive field of the previous layer.
* Multi-scale representation like HyperNet
    * Concatenate the output of the last layer and two intermediate layers, whose size are 2x and 4x of the last layer.
    * Set 2x layer as reference scale, down-scaling (pooing) 4x layer, up-scaling (interpolation) the last layer.

### Experiment
* Training details
    * Add Batch normalization layers before all ReLU.
    * Plateau detection based learning rate policy.
        * Measure the moving average of loss
        * Decide as *on-plateau* if its improvement is below a threshold.
        * Decrease the learning rate by a constant factor when *on-plateau*.
    * Number of proposals = 200
* VOC2007 & VOC2012 performance
    ![performance](http://img.blog.csdn.net/20161216125702361?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
