## Going deeper with convolutions
[paper link](http://arxiv.org/pdf/1409.4842.pdf)

> Famous paper of **GoogLeNet**. Partly inspired by [Network In Network](201608.md#network-in-network). Related blog post [here](http://wikicoursenote.com/wiki/GoingDeeperWithConvolutions).

### Motivation

1. Improving the performance by increasing the **depth** (more layers) and **size** (more filters per layer). But this has two drawbacks:
    * More prone to overfitting.
    * Dramatically increase computation.
2. To solve this, consider replacing fully connected with **sparse** ones (Based on [Provable bounds for learning some deep representations](http://jmlr.org/proceedings/papers/v32/arora14.pdf)).
    * This is still problematic because today's computing infrastructures are inefficient on non-uniform sparse data structures.
3. Should use an architecture of **filter-level sparsity**.

### Inception module
![picture here](http://wikicoursenote.com/w/images/8/8f/I1.png "Inception module, naiive version")

![picture here](http://wikicoursenote.com/w/images/b/b1/I2.png "Inception module with dimensionality reduction")

1. Make the feature to be processed at various scales and then aggregated. (Easy to understand)
2. Use 1x1 convolutions to reduce dimensionality thus require less computation. (The paper said dense and compressded representation is hard to process. *Does this means reducing dimensionality will also improve the performance?*)
3. Guiding principles??? Still not clear why the structure works as suggested in the paper.

### Network architecture
See the picture in the paper.

1. Move from fully connected to average pooling.
2. Use dropout!!!
3. Add auxiliary classifiers in the middle
    * Make the lower layer also discriminative.
    * Provide regularization. (*Why?*)
    * These loss are added to the total loss with a discount weight.

### Training details on ILSVRC classification

1. 7 independent versions (only differ in sampling methodologies and the random order).
2. Cropping approach in **test stage**:
    * 4 scales of origin image, with shorter dimension sized 256, 288, 320, 352 respectively;
    * Each takes the top, center, bottom squares;
    * Each square takes 4 corners and the center 224x224 crop as well as the square resized to 224x224;
    * Each crop takes origin and mirror version.
    * Leads to 4x3x6x2 = 144 crops per image.
3. Softmax averaged over multiple crops and all the individual classifiers (7 models, not different classifiers in the same network) in **test stage**.

### Result
Winner of 2015 ILSVRC. 6.67% error on test set.
