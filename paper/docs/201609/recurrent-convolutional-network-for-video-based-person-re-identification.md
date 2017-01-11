## Recurrent Convolutional Network for Video-based Person Re-Identification
* [paper link](http://pure.qub.ac.uk/portal/files/27151912/PID4180443.pdf)

![2016_09_20_201ded98f32b475e4f8468f9d3ae3a5](http://oa5omjl18.bkt.clouddn.com/2016_09_20_201ded98f32b475e4f8468f9d3ae3a5.png "Model structure")

### Model structure
* CNN and RNN as shown above
* Temporal pooling through RNN outputs
    * Average pooling
    * Max pooling (worse than baseline, one-shot)
    * **Can try attention**
* Siamese network
    * Pair input
    * **Can try triplet**
    ![2016_09_20_ea8f495c457b2ecd203e67e3c455e1d](http://oa5omjl18.bkt.clouddn.com/2016_09_20_ea8f495c457b2ecd203e67e3c455e1d.png "equation")
* Joint verification and identification
![equation](http://latex.codecogs.com/svg.latex?I%28v%29%3DP%28q%3Dc%7Cv%29%3D%5Cfrac%7B%5Cexp%28W_cv%29%7D%7B%5Csum_k%5Cexp%28W_kv%29%7D)
![equation](http://latex.codecogs.com/svg.latex?Q%28%5Cmathbf%7Bs%7D_1%2C%20%5Cmathbf%7Bs%7D_2%29%20%3D%20E%28R%28%5Cmathbf%7Bs%7D_1%29%2C%20R%28%5Cmathbf%7Bs%7D_2%29%29%2BI%28R%28%5Cmathbf%7Bs%7D_1%29%29%2BI%28R%28%5Cmathbf%7Bs%7D_2%29%29%0A)

### Experiment
* Datasets: [iLIDS-VID](http://www.eecs.qmul.ac.uk/~xz303/downloads_qmul_iLIDS-VID_ReID_dataset.html) and [PRID-2011](https://lrs.icg.tugraz.at/datasets/prid/)
* CNN pre-trained on Viper
* Settings
    * margin = 2
    * CNN encoding size = 128
    * learning rate = 1e-3
    * batch size = 1
    * epoch = 500 (one epoch = all positive pairs and the same number of negative pairs)
* Best setting: (RNN) Color+OF, mean pooling
* Cross dataset testing
* Currently state-of-the-art on iLIDS-VID and PRID-2011
