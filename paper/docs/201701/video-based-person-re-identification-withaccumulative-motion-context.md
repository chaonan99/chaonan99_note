## Video-based Person Re-identification with Accumulative Motion Context
* [paper](https://arxiv.org/pdf/1701.00193.pdf)

### Highlight
* Two stream: spatial + temporal (optical flow).
* Use a motion network pre-trained on optical flow to predict OF and also learn end-to-end in training phase.
* Fusion of motion and spatial features
* Multiloss: siamese reid and classification loss.

### Model
* Structure of the whole model:
    ![model](http://img.blog.csdn.net/20170105111604392?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* Structure of motion network (pre-trained on LK or Epic optical flow):
    ![motion network](http://img.blog.csdn.net/20170105111947936?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* Structure of spatial network:
    ![spatial network](http://img.blog.csdn.net/20170105112109051?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* Different spatial fusion method: concatenate, sum, max
* Different spatial fusion position: @ any layer in spatial network
* Motion context accumulation: via RNN (not LSTM in this paper)
* Multiloss: siamese (distance) loss + classification (softmax)
* Pre-train motion network on optical flow: smoothed L-1 loss (`l=1,2,3` representing optical flow estimation with different resolutions)
    * ![equation](http://latex.codecogs.com/svg.latex?L_%7B%28motion%29%7D%5E%7B%28l%29%7D%28e%5E%7B%28l%29%7D%2C%20g%5E%7B%28l%29%7D%29%3D%5Csum_%7Bi%2Cj%2Ck%7D%5Ctext%7Bsmooth%7D_%7BL_1%7D%28e%5E%7B%28l%29%7D_%7Bi%2Cj%2Ck%7D-g%5E%7B%28l%29%7D_%7Bi%2Cj%2Ck%7D%29)
    * ![equation](http://latex.codecogs.com/svg.latex?%5Ctext%7Bsmooth%7D_%7BL_1%7D%28%5Ctheta%29%3D%5Cbegin%7Bcases%7D0.5%5Ctheta%5E2%20%26%20%5Ctext%7Bif%20%20%7D%20%7C%5Ctheta%7C%3C1%20%5C%5C%20%7C%5Ctheta%7C-0.5%20%26%20%5Ctext%7Botherwise%7D%5Cend%7Bcases%7D)

### Experiment
* Datasets:
    * iLIDS-VID: 300 IDs, 2 camera views, sequence length 23~192
    * PRID-2011: 749 IDs, 2 camera views, sequence length 5~675
* Settings
    * Input of spatial net: 64 x 32; Input of motion net: 128 x 64
    * Data augmentation as both training and test phase
    * 10 times experiment on different training/test split
    * Sub-sequence 16 frames
    * Sequence length 128 for testing
* Ablation study
    * Motion information: compare LK & Epic OF, use OF as direct input or pre-train and train end-to-end. End-to-end training with Epic OF performs best.
    * Spatial fusion method and location: concatenate and fuse @Max-pooling2 performs better.
* Compare with state-of-the-art: new state-of-the-art on PRID-2011.