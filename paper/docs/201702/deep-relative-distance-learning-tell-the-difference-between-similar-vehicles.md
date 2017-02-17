## Deep Relative Distance Learning: Tell the Difference Between Similar Vehicles
* [paper](http://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Liu_Deep_Relative_Distance_CVPR_2016_paper.pdf)
* [dataset](https://www.pkuml.org/resources/pku-vehicleid.html)

### Highlight
* VGG, propose *coupled clusters loss*
* Multi-loss (car model, car ID)
* New dataset *VehicleID*

### Model
* Problem with triplet loss
    * When margin constraint already satisfied, the training sample makes no contribution to gradient decent.
    * Ancor point sensitive (negative point is pushed away according to the selected ancor and positive point).
* Coupled clusters loss
    * Samples belong to the same identity should locate around a common center point.
    * Center point
        *  $c^p = \frac{1}{N^p}\sum^{N^p}_i f(x^p_i)$
    * Coupled cluster loss
        *  $L(W, X^p, X^n)=\sum^{N^p}_i\frac12 \max\{0, \|f(x_i^p) - c^p\|_2^2+\alpha-\|f(x^n_*)-c^p\|^2_2\}$
        * $x_*^n$ is the nearest negative sample
* Two kinds of differences: same vehicle model & same identity
    * ![model structure](http://img.blog.csdn.net/20170217110407216?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

### Dataset
* VehicleID (newly proposed)
| Image number    | Training | Testing | All    |
|-----------------|----------|---------|--------|
| w\ model label  | 47558    |  42638  | 90196  |
| w\o model label | 67540    |  68947  | 136487 |
| All             | 110178   |  111585 | 226683 |


* CompCars
    * [dataset](http://mmlab.ie.cuhk.edu.hk/datasets/comp_cars/index.html)
    * [paper](http://arxiv.org/abs/1506.08959)
* Tasks
    * Vehicle model verification
    * Vehicle retrieval
    * Vehicle re-id