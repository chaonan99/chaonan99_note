# Dec. 22

## Detection
* Recognition by classification
* Localization by sliding window
* Challenge
    * Difficulties in recognition and localization
    * High computational complexity
* Target
    * High precision
    * High speed

## Development time line
* DPM: HoG based object detection
* Region proposal: selective search
    * Cut down the computational complexity of localization
* R-CNN
    * Selective search to do region proposal, 2k proposal per image
    * Resize regions to square (fixed size for VGG-16)
    * VGG-16 feature extraction
    * Performance
* Spatial pyramid network (Kaiming He, Xiangyu Zhang, Shaoqing Ren)
    * Region proposal on feature map
    * Limitation: SPP layer can only forward
* Fast R-CNN
    * Redefine SPP layer that support back-propogation
    * Still use selective search and VGG-16
    * Bottleneck: region proposal (two research line)
        * Selective search
        * Edge box
* Faster R-CNN
    * See [paper note](../../paper/201611.md)
    * Faster RNN divide the whole CNN into region proposal part and classification part (101 = 91+10), 10 layer classifier need to run many times (number of proposals)
* [R-FCN](http://cn.arxiv.org/pdf/1605.06409v2)
* Other paper
    * Overfeat
    * Scalable object detection
    * You only look once
    * SSD
    * Feature pyramid networks for object deteciton

## Momenta
* 