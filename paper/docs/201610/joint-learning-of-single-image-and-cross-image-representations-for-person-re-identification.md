## Joint Learning of Single-image and Cross-image Representations for Person Re-identification

![2016_10_14_57c771e82f299fbfd24bc07f946e486c](http://oa5omjl18.bkt.clouddn.com/2016_10_14_57c771e82f299fbfd24bc07f946e486c.png)

![2016_10_14_8d78afec4a3594b3eb45ba283cdf7](http://oa5omjl18.bkt.clouddn.com/2016_10_14_8d78afec4a3594b3eb45ba283cdf7.png)

### Intuition
* Re-id method: single-image representation (SIR) and cross-image representation (CIR).
* Combine them together!

### Method
* SIR measurements are special cases of CIR-based classification.
    * SIR(Euclidean distance): ![equation](http://latex.codecogs.com/svg.latex?S_%7BSIR%7D%28x_i%2Cx_j%29%3D%7C%7Cf%28x_i%29-f%28x_j%29%7C%7C_2%5E2)
    * CIR: ![equation](http://latex.codecogs.com/svg.latex?S_%7BCIR%7D%28x_i%2Cx_j%29%3Dw%5ETg%28x_i%2Cx_j%29-b)
* Also combine pairwise loss and triplet loss.
    * Pairwise
        * ![equation](http://latex.codecogs.com/svg.latex?L_%7BSIR%7D%5EP%3D%5Csum_%7Bi%2Cj%7D%5B1%2Bh_%7Bij%7D%28%7C%7Cf%28x_i%29-f%28x_j%29%7C%7C_2%5E2-b_%7BSIR%7D%29%5D_%2B)
        * ![equation](http://latex.codecogs.com/svg.latex?L_%7BCIR%7D%5EP%3D%5Cfrac%7B%5Calpha_P%7D%7B2%7D%7C%7Cw%7C%7C_2%5E2%2B%5Csum_%7Bi%2Cj%7D%5B1%2Bh_%7Bij%7D%28w%5ETg%28x_i%2Cx_j%29-b_%7BSIR%7D%29%5D_%2B)
        * where ![equation](http://latex.codecogs.com/svg.latex?b_%7BSIR%7D%2Cb_%7BCIR%7D) is the distance threshold (margin), ![equation](http://latex.codecogs.com/svg.latex?%5Calpha_P) is the trade-off parameter, which is set to 0.0005 in the experiments
        * Combine: ![equation](http://latex.codecogs.com/svg.latex?L%5EP%3DL_%7BSIR%7D%5EP%2B%5Ceta_PL_%7BCIR%7D%5EP)
    * Triplet
        * ![equation](http://latex.codecogs.com/svg.latex?L_%7BSIR%7D%5ET%3D%5Csum_%7Bi%2Cj%2Ck%7D%5Bb_%7BSIR%7D-%7C%7Cf%28x_i%29-f%28x_k%29%7C%7C_2%5E2%2B%7C%7Cf%28x_i%29-f%28x_j%29%7C%7C_2%5E2%29%5D_%2B)
        * ![equation](http://latex.codecogs.com/svg.latex?L_%7BCIR%7D%5ET%3D%5Cfrac%7B%5Calpha_P%7D%7B2%7D%7C%7Cw%7C%7C_2%5E2%2B%5Csum_%7Bi%2Cj%2Ck%7D%5Bb_%7BCIR%7D%2Bw%5ETg%28x_i%2Cx_k%29-w%5ETg%28x_i%2Cx_j%29%5D_%2B)
        Combine: ![equation](http://latex.codecogs.com/svg.latex?L%5ET%3DL_%7BSIR%7D%5ET%2B%5Ceta_TL_%7BCIR%7D%5ET)
* Compute cross-image feature map
    ![equation](http://latex.codecogs.com/svg.latex?%5Cvarphi_r%28x_i%2Cx_j%29%3Dmax%280%2Cb_r%2B%5Csum_qk_%7Bq%2Cr%7D%2A%5Cphi_q%28x_i%29%2Bl_%7Bq%2Cr%7D%2A%5Cphi_q%28x_j%29%29)

### Result
* Dataset: CUHK-01/03, VIPeR.
* 52.17% on CUHK03.
* Investigation on sensitivity of trade-off parameter.
* 71.8% on CUHK01 (pretrain on CUHK03).
* 35.76% on VIPeR.