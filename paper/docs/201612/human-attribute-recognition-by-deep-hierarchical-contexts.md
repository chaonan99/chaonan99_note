## Human Attribute Recognition by Deep Hierarchical Contexts
* [ECCV 2016](http://www.eccv2016.org/main-conference/)
* [paper](http://personal.ie.cuhk.edu.hk/~ccloy/files/eccv_2016_human.pdf)
* [poster](http://www.eccv2016.org/files/posters/P-4A-21.pdf)
* Author: Yining Li, [Chen Huang](http://mmlab.ie.cuhk.edu.hk/html_people/research_fellow_Chen_Huang.html), [Chen Change Loy](http://personal.ie.cuhk.edu.hk/~ccloy/), and [Xiaoou Tang](https://www.ie.cuhk.edu.hk/people/xotang.shtml)
* [CUHK multimedia lab](http://mmlab.ie.cuhk.edu.hk/index.html)

### Model
* Use VGG-16.
* Input whole image and conduct ROI pooling to get features for different parts.
* Four different VGGs:
    * Whole image;
    * Person bbox;
    * Part-based bbox;
    * Similar bbox from other persons.
* Attribute cross entropy loss.
* Details:
    * Use ground truth person bbox
    * Use [Poselet](https://www2.eecs.berkeley.edu/Research/Projects/CS/vision/shape/poselets/) to generate part bbox

### Datasets
* Propose [WIDER attribute](http://mmlab.ie.cuhk.edu.hk/projects/WIDERAttribute.html).
* [Berkeley Person Attribute](https://www2.eecs.berkeley.edu/Research/Projects/CS/vision/shape/poselets/).
* [HAT](https://jurie.users.greyc.fr/datasets/hat.html).

### Experiment
* Current state-of-the-art on BPA, HAT and WIDER.
