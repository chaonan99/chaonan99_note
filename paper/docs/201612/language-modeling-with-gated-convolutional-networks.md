## Language Modeling with Gated Convolutional Networks
* [paper](http://arxiv.org/pdf/1612.08083v1)
* CNN beats LSTM in language model?

### Model
* ![Model](http://img.blog.csdn.net/20161230161832163?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* Word embedding
* Hidden layers: $h_l(X)=(X*W+b) \bigotimes \sigma(X*V+c)$
    * $\bigotimes$: element-wise product
    * $W,V \in \mathbb{R}^{k\times m\times n}$
    * Note that the begin of the sequence is zero-padded by `k/2`
    * The linear gate can alleviate vanishing gradient problem (can be seen as a multiplicative skip connection)
* Adaptive softmax

### Experiment
* Datasets: Google Billion Word (GBW), WikiText-103
* Optimization: Nesterov's momentum, gradient clipping (to 0.1), weight normalization
    * Can gain stable and fast convergence with large learning rate such as 1
* Hyper-parameter search
* Result
    * Speed: GCNN-22 compared with LSTM-2048 (units), better throughput and responsiveness
    * Complexity: GCNN-22 compared with LSTM-2048 (units), less parameter and FLOPs/token
    * Gating mechanism: GLU > (GTU (LSTM unit) <=> ReLU) > Tanh
    * Non-linear modeling: GLU > Linear > Bilinear
    * Network depth: the deep the better
    * Context: large context size brings lower test perplexity but returns diminish.