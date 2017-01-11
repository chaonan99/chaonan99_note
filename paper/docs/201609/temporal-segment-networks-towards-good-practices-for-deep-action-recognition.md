## Temporal Segment Networks: Towards Good Practices for Deep Action Recognition
* [paper link](https://arxiv.org/pdf/1608.00859v1.pdf)

### Model
* Based on [two-stream](https://arxiv.org/abs/1406.2199)
* Equally divide into `K` segments
    * This is like independently evaluate on three videos and combine their possibilities together via aggregation function (below).
* Aggregation function `g` (averaging, maximum, and weighted averaging)
* Modalities
    * RGB (static info)
    * RGB difference between two consecutive frames (appearance change)
    * Optical flow
    * Wrapped OF (estimating homography matrix and compensating camera motion)
* Cross-modality pre-training (utilize RGB models to initialize the temporal networks)
* Batch-normalization
* Data augmentation
    * Corner cropping (choose corner or center, not only center)
    * Multi-scale cropping (select cropping scale {256, 224, 192, 168}), finally resized to 224 * 224

### Experiments
* Datasets: HMDB51, UCF101
* Settings (Sec 4.1)
    * Number of segments `K = 3`
* Different training strategy
    * From scratch
    * Pre-train spatial stream
    * Cross-modality pre-training
    * (Best) Combination of cross modality pre-training and partial BN with dropout
* Different aggregation function (max, average, weighted average pooling)
* Different modalities (RGB, RGB diff, optical flow, warped optical flow)
    * With RGB+of+wof performs best (RGB diff harm performance)
* Different CNN (BN-Inception, VGG-16, GoogLeNet)
* Compare with state-of-the-art
* (Interesting) Using [DeepDraw](https://github.com/auduno/deepdraw) to do class level visualization