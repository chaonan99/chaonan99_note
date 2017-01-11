## Visualizing and Understanding Convolutional Networks
[paper link](https://arxiv.org/pdf/1311.2901v3.pdf)

![2016_08_29_9fe8c0e8b9b8ac8f6dcfc189ae6cd1](http://oa5omjl18.bkt.clouddn.com/2016_08_29_9fe8c0e8b9b8ac8f6dcfc189ae6cd1.png "Model of this paper")

### Approach
Deconv net. Use a trained model, feed an image and deconv back to get feature map.
For different layers, method of deconv:

1. **Pooling** When forwarding the image, recording the locations of the maxima within each pooling region in a set of switch variables. Use switch for unpooling when backwarding.
2. **Relu** Relu again (*Why?*).
3. **Conv** Convolution operation with transposed version of the same filter (*Why?*).
4. **Contrast norm** Do not use any contrast normalization operations when in this
reconstruction path (this statement has been deleted in the newest version, *why?*)

### Result

1. The author improve the previous model and get better result on ImageNet, especially better features in 1st/2nd layers.
2. Extract feature map after different epoches, find that higher level features need more epoch to learn.
3. (Seems irrelevent to the visualization tool) Do geometric transformation and feed images to CNN, calculate Euclidean distance of features. Find that ConvNet has some invariance to translation (more invariance gained in higher layer) and scaling, but not on rotation, .
