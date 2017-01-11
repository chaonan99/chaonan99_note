## Human-In-The-Loop Person Re-Identification
* [ECCV 2016](http://www.eccv2016.org/main-conference/)
* [Paper](http://www.eecs.qmul.ac.uk/~xz303/papers/ECCV16/WangEtAl_ECCV2016.pdf)
* [Poster](http://www.eccv2016.org/files/posters/P-2B-41.pdf)
* Author: [Hanxiao Wang](http://www.eecs.qmul.ac.uk/~hw304/#bio), [Shaogang Gong](http://www.eecs.qmul.ac.uk/~sgg/), Xiatian Zhu, [Tao (Tony) Xiang](https://www.eecs.qmul.ac.uk/~txiang/)

> Professor Shaogang Gong from [Queen Mary, University of London](http://www.eecs.qmul.ac.uk/), who works closely with Dr. Tony Xiang, is an expert in person re-id field. He wrote a book naming [Person Re-Identification](http://link.springer.com/book/10.1007%2F978-1-4471-6296-4). Since this book has been published, supervised learning method with CNN feature extractor has gradually dominate this field (person re-id). However, prof. Gong and his group are seeking for novel ways to resolve re-id problem. They have two papers about person re-id in ECCV 2016, together with [Person Re-identification by Unsupervised L1 Graph Learning](http://www.eecs.qmul.ac.uk/~sgg/papers/KodirovEtAl_ECCV2016.pdf), both do not follow the supervised learning scheme.

![model pipe line](http://img.blog.csdn.net/20161028124735051)

### Highlight
* Propose Human Verification Incremental Learning (HVIL), an **online learning** approach for person re-id.
* Do not need labeled data. Human participates in the training procedure, to give a pair of probe-gallery image a feedback as **true, similar(but not true), dissimilar**.
* Small training set, large test set.
* They show some other works attempting to relax the need of labeling, with semi-supervised, unsupervised and transfer learning approches, in Related Work part.

### Modeling human feedback as a loss function
* Incrementally optimised ranking function
    ![equation](http://latex.codecogs.com/svg.latex?err%28f_%7Bx%5Ep%7D%28x%5Eg%29%2C%20y%29%3D%5Cmathcal%7BL%7D_y%28rank%28f_%7Bx%5Ep%7D%28x%5Eg%29%29%29)
    where ![equation](http://latex.codecogs.com/svg.latex?f_%7Bx%5Ep%7D%28x%5Eg%29) is the distanse of pair ![equation](http://latex.codecogs.com/svg.latex?%5C%7Bx%5Ep%2C%20x_g%5C%7D), which is defined as negative [Mahalanobis Distance](https://en.wikipedia.org/wiki/Mahalanobis_distance). ![equation](http://latex.codecogs.com/svg.latex?y) denotes the feedback, that is, ![equation](http://latex.codecogs.com/svg.latex?y%5Cin%20) {true-match, strong-negative, week-negative} ({m,s,w}). ![equation](http://latex.codecogs.com/svg.latex?rank) is just an int number denotes the rank of a gallery image.
* Re-id ranking loss ![equation](http://latex.codecogs.com/svg.latex?%5Cmathcal%7BL%7D_y) is defined as
    ![equation](http://latex.codecogs.com/svg.latex?%5Cbegin%7Balign%2A%7D%0A%09%5Cmathcal%7BL%7D_y%28k%29%26%3D%5Csum_%7Bi%3D1%7D%5Ek%20%5Calpha_i%09%5Cquad%20if%5Cquad%20y%5Cin%20%5C%7Bm%2Cw%5C%7D%5C%5C%0A%09or%20%26%3D%5Csum_%7Bi%3Dk%2B1%7D%5E%7Bn_g%7D%5Calpha_i%20%5Cquad%20if%20%5Cquad%20y%5Cin%20%5C%7Bs%5C%7D%0A%09%5Cend%7Balign%2A%7D)
    with ![equation](http://latex.codecogs.com/svg.latex?%5Calpha_1%5Cgeq%20%5Calpha_2%5Cgeq%20%5Cdots%20%5Cgeq%200)

### Real-time Model Update for Instant Feedback Reward
* Negative Mahalanobis Distance:
    ![equation](http://latex.codecogs.com/svg.latex?f_%7Bx%5Ep%7D%28x%5Eg%29%3D-%5B%28x%5Ep-x%5Eg%29%5E%5Cmathbf%7BT%7DM%28x%5Ep-x%5Eg%29%5D%2C%20M%5Cin%20S%5Ed_%2B)
    ![equation](http://latex.codecogs.com/svg.latex?S%5Ed_%2B) represents semi-definate matrix.
* Knowledge cumulation by online learning
    ![equation](http://latex.codecogs.com/svg.latex?M_t%3D%5Cunderset%7BM%5Cin%20S%5Ed_%2B%7D%7B%5Carg%5Cmin%7D%5CDelta_F%28M%2CM_%7Bt-1%7D%29%2B%5Ceta%5Cmathcal%7BL%7D%5E%7B%28t%29%7D)
    This equation with ![equation](http://latex.codecogs.com/svg.latex?t) indicate that the matrix ![equation](http://latex.codecogs.com/svg.latex?M) in M-distance is learned in stages (knowledge cumulation). ![equation](http://latex.codecogs.com/svg.latex?%5Cmathcal%7BL%7D%5E%7B%28t%29%7D) is the loss of human feed back in ![equation](http://latex.codecogs.com/svg.latex?t) stage. ![equation](http://latex.codecogs.com/svg.latex?%5CDelta_F) is [Burg matrix divergence](https://en.wikipedia.org/wiki/Bregman_divergence)??
    ![equation](http://latex.codecogs.com/svg.latex?%5CDelta_F%28M%2C%20M_%7Bt-1%7D%29%3Dtr%28MM_%7Bt-1%7D%5E%7B-1%7D%29-logdet%28MM_%7Bt-1%7D%5E%7B-1%7D%29)

### Metric ensemble learning
* When no human feedback is avilable.
* Idea: re-using pairs already verified by human
    ![equation](http://latex.codecogs.com/svg.latex?f_%7Bij%7D%5E%7Bens%7D%3Df_%7Bx_i%5Ep%7D%5E%7Bens%7D%28x_j%5Eg%29%3D-d_%7Bij%7D%5E%7B%5Cmathbf%7BT%7D%7DWd_%7Bij%7D)
* Ideal ranking: ![equation](http://latex.codecogs.com/svg.latex?f_%7Bij%7D%5E%2A%3D0) for ![equation](http://latex.codecogs.com/svg.latex?c_i%3Dc_j) and ![equation](http://latex.codecogs.com/svg.latex?f_%7Bij%7D%5E%2A%3D-1) for ![equation](http://latex.codecogs.com/svg.latex?c_i%5Cneq%20c_j).

### Experiment
* Settings
    * For human feedback, 300 people/image probe; 1000 people/image gallery. Return top-50 in the rank list for feedback.
    * Max 3 rounds for each probe, result in 300-900 indicative verification.
* Claim that suer input will be 10-fold less.
* Better than other human-in-the-loop methods. Less feedback and search time.
* 56.1% on CUHK-03, 78% on Market-1501.
* Evaluate automated person re-id
    * 168 pairs on CUHK-03, 234 pairs on Market-1501; supervised model trained with 300 ground truth data for comparison.
    * Also compared with unensembled matrix after ![equation](http://latex.codecogs.com/svg.latex?%5Ctau) (![equation](http://latex.codecogs.com/svg.latex?M_%7B%5Ctau%7D)) and average matrix ![equation](http://latex.codecogs.com/svg.latex?M) for all time ![equation](http://latex.codecogs.com/svg.latex?1-%5Ctau) (![equation](http://latex.codecogs.com/svg.latex?M_%7Bavg%7D))
    * Ensembled performs best.
