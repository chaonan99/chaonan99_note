## Hierarchical Recurrent Neural Encoder for Video Representation with Application to Captioning
[paper link](http://arxiv.org/pdf/1511.03476v1.pdf)

![2016_09_01_f5f769c9ad886f8d209bf7d3a425969](http://oa5omjl18.bkt.clouddn.com/2016_09_01_f5f769c9ad886f8d209bf7d3a425969.png "Intuition")

![2016_09_01_90d89552e015c34e67806a4845e0b587](http://oa5omjl18.bkt.clouddn.com/2016_09_01_90d89552e015c34e67806a4845e0b587.png "Whole network")

> Re-read this to get the intuition of current working model.

### Intuitions

1. The author argue that the following solutions to extract temporal information are lack of long term temporal dependency. We need to model video temporal structure with multiple granularities.
    * Two-stream (optical flow is expensive and only short duration feature)
    * 3D Convnet ([Should have a link after reading this])
    * VLAD (know nothing)
2. LSTM can deal with long video, but the **favorable length is 30~80 frames**.
3. Additional non-linearity is helpful, so we can stack LSTMs.

### Model
* Picture one, using stride (= 8) with attention as the input to the first layer lstm (number of steps set to 8).
* Every next layer, use stride to divide previous output into several groups, and use attention on the group to make input.
* Whole model has 2 layers.

### Result
Compare with FGM, Meanpool, SA, S2VT, LSTM-E, p-RNN. The performance is similar with p-RNN on MSVD.
