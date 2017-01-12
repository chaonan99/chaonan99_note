## Learning from Simulated and Unsupervised Images through Adversarial Training
* [paper](http://arxiv.org/pdf/1612.07828v1.pdf)
* This is (probably?) the first paper from Apple in ML/CV field

### Contribution
* Propose Simulate + Unsupervised training, using real world images to refine the synthetic images, with GAN
* Training GAN using adversarial loss and a self-regularization loss
* Key modifications to stabilize GAN training and prevent artifacts

### Framework
* Refiner (Generator): $\tilde{x}:=R_\theta(x)$
* Refiner loss (general formular): $\mathcal{L}_R(\theta)=\sum_i l_{real}(\theta; \tilde{x}_i, \mathcal{Y})+\lambda l_{reg}(\theta; \tilde{x}_i, x_i)$
    * $l_{reg}$ minimizing the difference between the synthetic and the refined images
* Discriminator Loss: $\mathcal{L}_D(\phi) = -\sum_i \log(D_{\phi} (\tilde{x}_i)) - \sum_j \log(1-D_{\phi}(y_j))$
    * `x~_i, y_j` are randomly sampled from refined images and real images sets
* Algorithm:
    * ![algorithm](http://img.blog.csdn.net/20161229114626218?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* `L_R` loss in the implementation of this paper: $\mathcal{L}_R(\theta)=\sum_i \log(1-D_{\phi}(R_{\theta}(x_i)))+\lambda||R_{\theta}(x_i)-x_i||_1$

### Stabilize GAN training
* Local adversarial loss: divide the refined image and real image into `w x h` regions and use separate discriminators to judge each region
    * ![local adversarial loss](http://img.blog.csdn.net/20161229115211830?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
    * Final loss is the sum of loss on each region
* Using history of refined images
    * Two issues when only use the latest refined images
        * Diverging of adversarial training
        * The refiner network re-introducing the artifacts that the discriminator had forgotten about
    * Buffer history images, use `b/2` history images and `b/2` newly refined images in each iter
    * Update `b/2` of the buffered images in each iter

### Experiments
* Gaze estimation
    * Dataset: MPIIGaze dataset
    * Synthesizer: UnityEyes
    * Visual Turing test: human cannot tell the difference between refined and real images
    * Quantitative result: 22.3% percentage of improvement
* Hand pose estimation
    * Dataset: NYU hand pose dataset
    * Training CNN: Hour glass network