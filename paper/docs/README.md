# Welcome to My Paper Note

This note is now build with [MkDocs](http://www.mkdocs.org/).

To install and build this note:

* Install MkDocs

```
pip install mkdocs
```

* Install Python-Markdown. To correctly render this note, please install [my fork](https://github.com/chaonan99/python-markdown-math) of this extension (I am used to `$$` for inline math and `$$$$` for stand alone).

```
git clone https://github.com/chaonan99/python-markdown-math.git
cd python-markdown-math
python setup.py build
python setup.py install
```

* Use mkdocs' server to view the note (in paper dir)

```
mkdocs serve
```

Here are some useful mkdocs command.

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs help` - Print this help message.

# Paper list

[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

## ReID
* [Video-based Person Re-identification with Accumulative Motion Context](201701/video-based-person-re-identification-withaccumulative-motion-context.md) \[[paper](https://arxiv.org/pdf/1701.00193.pdf)\]
* [Deep Attributes Driven Person Re-identification](201610/deep-attributes-driven-person-re-identification.md) \[[paper](https://arxiv.org/pdf/1605.03259v2.pdf)\] \[[poster](http://www.eccv2016.org/files/posters/P-1B-34.pdf)\]
* [Human-In-The-Loop Person Re-Identification](201610/human-in-the-loop-person-re-identification.md) \[[paper](http://www.eecs.qmul.ac.uk/~xz303/papers/ECCV16/WangEtAl_ECCV2016.pdf)\] \[[poster](http://www.eccv2016.org/files/posters/P-2B-41.pdf)\]
* [Embedding Deep Metric for Person Re-identification: A Study Against Large Variation](201610/embedding-deep-metric-for-person-re-identification-a-study-against-large-variation.md)
 \[[paper](http://www.cbsr.ia.ac.cn/users/hailinshi/papers/2016-eccv/0236.pdf)\] \[[poster](http://www.eccv2016.org/files/posters/P-1A-44.pdf)\]
* [Joint Learning of Single-image and Cross-image Representations for Person Re-identification](201610/joint-learning-of-single-image-and-cross-image-representations-for-person-re-identification.md) \[[paper](http://ss.sysu.edu.cn/~ll/files/CVPR2016_PersonReID.pdf)\]
* [Gated Siamese Convolutional Neural Network Architecture for Human Re-Identification](201610/gated-siamese-convolutional-neural-network-architecture-for-human-re-identification.md) \[[paper](https://arxiv.org/pdf/1607.08378v2.pdf)\]
* [Recurrent Convolutional Network for Video-based Person Re-Identification (Need picture)](201609/recurrent-convolutional-network-for-video-based-person-re-identification.md)
* [End-to-End Comparative Attention Networks for Person Re-identification](201609/end-to-end-comparative-attention-networks-for-person-re-identification.md)
* [Recurrent Models of Visual Attention](201608/recurrent-models-of-visual-attention.md)

## Language
* [LSTM: A Search Space Odyssey]()
* [Language Modeling with Gated Convolutional Networks](201612/language-modeling-with-gated-convolutional-networks.md) \[[paper](http://arxiv.org/pdf/1612.08083v1)\]
* [Memory Networks](201609/memory-networks.md)

## GAN
* [Learning from Simulated and Unsupervised Images through Adversarial Training](201612/learning-from-simulated-and-unsupervised-images-through-adversarial-training.md) \[[paper](http://arxiv.org/pdf/1612.07828v1.pdf)\]

## Detection
* [Feature Pyramid Networks for Object Detection](201612/feature-pyramid-networks-for-object-detection.md) \[[paper](http://arxiv.org/pdf/1612.03144v1)\]
* [PVANET: Deep but Lightweight Neural Networks for Real-time Object Detection](201612/pvanet-deep-but-lightweight-neural-networks-for-real-time-object-detection.md) \[[paper](http://cn.arxiv.org/pdf/1608.08021v3)\]
* [Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks](201609/faster-r-cnn-towards-real-time-object-detection-with-region-proposal-networks.md)

## Segmentation/Parsing
* [RefineNet: Multi-Path Refinement Networks for High-Resolution Semantic Segmentation](201612/refinenet-multi-path-refinement-networks-for-high-resolution-semantic-segmentation.md) \[[paper](http://arxiv.org/pdf/1611.06612v3.pdf)\]
* [Pyramid Scene Parsing Network](201612/pyramid-scene-parsing-network.md) \[[paper](https://arxiv.org/pdf/1612.01105.pdf)\]

## CNN Architecture
* [Aggregated Residual Transformations for Deep Neural Networks](201612/aggregated-residual-transformations-for-deep-neural-networks.md) \[[paper](http://cn.arxiv.org/pdf/1611.05431v1)\]
* [Xception: Deep Learning with Depthwise Separable Convolutions](201612/xception-deep-learning-with-depthwise-separable-convolutions.md) \[[paper](http://cn.arxiv.org/pdf/1610.02357v2)\]
* [Densely Connected Convolutional Networks](201612/densely-connected-convolutional-networks.md) \[[paper](http://cn.arxiv.org/pdf/1608.06993v3)\]
* [Going deeper with convolutions](201608/going-deeper-with-convolutions.md)
* [Network In Network](201608/network-in-network.md)
* [Visualizing and Understanding Convolutional Networks](201608/visualizing-and-understanding-convolutional-networks.md)

## Benchmark
* [MARS: A Video Benchmark for Large-Scale Person Re-identification](201701/mars-a-video-benchmark-for-large-scale-person-re-identification.md) \[[paper](http://liangzheng.org/1320.pdf)\] \[[code](https://github.com/liangzheng06/MARS-evaluation)\]
* [Human Attribute Recognition by Deep Hierarchical Contexts (WIDER)](201612/human-attribute-recognition-by-deep-hierarchical-contexts.md) \[[paper](http://personal.ie.cuhk.edu.hk/~ccloy/files/eccv_2016_human.pdf)\] \[[webpage](http://mmlab.ie.cuhk.edu.hk/projects/WIDERAttribute.html)\]
* [Microsoft Video Description Corpus (MSVD)](201609/microsoft-video-description-corpus-msvd.md)
* [Tumblr GIF (TGIF)](201609/tumblr-gif-tgif.md)
* [Microsoft Research - Video to Text (MSR-VTT)](201609/microsoft-research-video-to-text-msr-vtt.md)
* [Market-1501](201609/market-1501.md)


## Image/Video Caption
* [Hierarchical Recurrent Neural Encoder for Video Representation with Application to Captioning](201609/hierarchical-recurrent-neural-encoder-for-video-representation-with-application-to-captioning.md)
* [Describing Videos by Exploiting Temporal Structure](201609/describing-videos-by-exploiting-temporal-structure.md)

## Other
* [Temporal Segment Networks: Towards Good Practices for Deep Action Recognition](201609/temporal-segment-networks-towards-good-practices-for-deep-action-recognition.md)