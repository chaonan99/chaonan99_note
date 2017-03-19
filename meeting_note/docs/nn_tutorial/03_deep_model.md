# Model Design

## Design rule
* FC can turn to conv

## GoogLeNet
* Less #OP, smaller size
* Inception layer
* Layer structure is too complicated
* Average pooling to decrease feature map size
    * Bad in character recognition

## Waterfall
* Developed by Xiangyu

## OCR

### Traditional
* Need assumptions
    * Plain layout
    * Good light condition
* Align well designed document (e.g. bills)
* Problem
    * Complex layout
    * Handwritten
    * Multilingual

### NN
* Most time spend on build dataset
* Heat map is easy to train
* Chinese character challenge
    * Left-right structure (萌：明，月)
