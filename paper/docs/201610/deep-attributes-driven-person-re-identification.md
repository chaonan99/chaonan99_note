## Deep Attributes Driven Person Re-identification
* [ECCV 2016](http://www.eccv2016.org/main-conference/)
* [paper](https://arxiv.org/pdf/1605.03259v2.pdf)
* [poster](http://www.eccv2016.org/files/posters/P-1B-34.pdf)
* Author: Chi Su, [Shiliang Zhang](http://www.idm.pku.edu.cn/staff/zhangshiliang/team/team.html), Junliang Xing, Wen Gao1, and [Qi Tian](http://www.cs.utsa.edu/~qitian/)

### Intuition
* Low level feature sensitive to viewpoint, body poses, etc., and have different character corresponding to different metric learning methods.
* Attribute is mid-level feature.
* Problem:  it is difficult to acquire enough training data for a large set of attributes.
* Related work: deep attribute learning works.
### Three stage model
![three stage model](http://img.blog.csdn.net/20161028143951960)

* Goal: learn an attribute predict model for person ReID through dCNN training
    ![equation](http://latex.codecogs.com/svg.latex?A_I%3D%5Cmathcal%7BO%7D%28I%29)
* First stage: train on attribute dataset
    * AlexNet
    * Dataset ![equation](http://latex.codecogs.com/svg.latex?T%3D%5C%7Bt_1%2Ct_2%2C%5Cdots%2Ct_N%5C%7D) labeled with a binary attribute.
    * Get trained model ![equation](http://latex.codecogs.com/svg.latex?%5Cmathcal%7BO%7D%5E%7BS1%7D), which could predict attribute for any test sample but lack discriminative power.
* Second stage: fine-tuning on person ID dataset
    * Dataset ![equation](http://latex.codecogs.com/svg.latex?U%3D%5C%7Bu_1%2Cu_2%2C%5Cdots%2Cu_M%5C%7D) has person ID label.
    * Only set attributes with top ![equation](http://latex.codecogs.com/svg.latex?p%3D10) highest confidence score as 1, others as 0.
    * Triplet loss
        ![equation](http://latex.codecogs.com/svg.latex?%5Cmathcal%7BL%7D%20%3D%20%5Csum_e%5EE%5C%7B%5Cmax%280%2C%20D%28A%5E%7B%28e%29%7D_%7B%28a%29%7D%2C%20A%5E%7B%28e%29%7D_%7B%28p%29%7D%29%2B%5Ctheta-D%28A%5E%7B%28e%29%7D_%7B%28a%29%7D%2C%20A%5E%7B%28e%29%7D_%7B%28n%29%7D%29%29%2B%5Cgamma%5Ctimes%20%5Cvarepsilon%5C%7D)
        ![equation](http://latex.codecogs.com/svg.latex?%5Cvarepsilon%3DD%28A%5E%7B%28e%29%7D_%7B%28a%29%7D%2C%20%5Ctilde%7BA%7D%5E%7B%28e%29%7D_%7B%28a%29%7D%29%2BD%28A%5E%7B%28e%29%7D_%7B%28p%29%7D%2C%20%5Ctilde%7BA%7D%5E%7B%28e%29%7D_%7B%28p%29%7D%29%2BD%28A%5E%7B%28e%29%7D_%7B%28n%29%7D%2C%20%5Ctilde%7BA%7D%5E%7B%28e%29%7D_%7B%28p%29%7D%29)
        where ![equation](http://latex.codecogs.com/svg.latex?%5Ctheta%3D1), ![equation](http://latex.codecogs.com/svg.latex?%5Cgamma%3D0.01) in the experiment setting.
    * Get model ![equation](http://latex.codecogs.com/svg.latex?%5Cmathcal%7BO%7D%5E%7BS2%7D)
* Third stage: fine-tuning on the Combined Dataset
    * First predict attributes for dataset ![equation](http://latex.codecogs.com/svg.latex?U) using ![equation](http://latex.codecogs.com/svg.latex?%5Cmathcal%7BO%7D%5E%7BS2%7D), act as ground truth attributes.
    * Combine ![equation](http://latex.codecogs.com/svg.latex?T) and ![equation](http://latex.codecogs.com/svg.latex?U) as a big attribute dataset, training to get final *deep attribute* extractor ![equation](http://latex.codecogs.com/svg.latex?%5Cmathcal%7BO%7D)

### Experiment
* Attribute dataset in first stage: PETA, split multi-class attribute into binary attributes.
* Tracking dataset in second stage: MOT challenge
* Attribute accuracy
    ![attribute accuracy](http://img.blog.csdn.net/20161028151836383)
* Evaluate: VIPeR, PRID, GRID, Market-1501 (VIPeR, GRID and PRID are included in the PETA dataset, they will be excluded from PETA during training)
* XQDA metric learning method, further improvement
* Datasets: VIPeR (43.5%, `sor`->63.9%), PRID 450S (22.6%, `sor`->60%+), Market (Single: 39.4%, multiple: 49.0%, `sor`->78%)
    * `sor` denotes state-of-the-art
    * The model does not use these three dataset for training, thus it cannot compare directly with supervised re-id model.
* Additional experiments
    * Combine hand-crafted feature with *deep attribute*, improve about 8% on VIPeR.
    * Directly fine-tune FC7 feature of AlexNet, *deep attribute* performs better.
