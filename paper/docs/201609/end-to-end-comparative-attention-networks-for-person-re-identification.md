## End-to-End Comparative Attention Networks for Person Re-identification
* [paper link](https://arxiv.org/pdf/1606.04404v1.pdf)

### Model structure
![2016_09_18_b2a7c855d76fd2d0fd9fc4ab8a7e92c](http://oa5omjl18.bkt.clouddn.com/2016_09_18_2016_09_18_b2a7c855d76fd2d0fd9fc4ab8a7e92c.png "2016_09_18_b2a7c855d76fd2d0fd9fc4ab8a7e92c")

![2016_09_18_b7ecb6331c92ce2ad9ae321dc346](http://oa5omjl18.bkt.clouddn.com/2016_09_18_b7ecb6331c92ce2ad9ae321dc346.png "Add Description")

* Use AlexNet Max-5 feature (6 * 6 * 256)
* LSTM with attention
    * **Same image feature** at every time step (total time steps T=8)
    * Attention only conditioned on previous time step
    * Extract (2nd, 4th, 8th)/all/last hidden state and concatenated as the final features passed to the normalization layer (2,4,8 being the best)
* Re-id triplet method
    * Anchor I, positive I+, negative I-
    * Loss: ![2016_09_18_5740ab76c07ddde2b58ab5ef13af4081](http://oa5omjl18.bkt.clouddn.com/2016_09_18_5740ab76c07ddde2b58ab5ef13af4081.png "Re-id loss")

### Experiment
* Dataset: CUHK01, CUHK03, Market-1501
* Settings: see Sec.IV-B
* Result: Great improvements on all three datasets
