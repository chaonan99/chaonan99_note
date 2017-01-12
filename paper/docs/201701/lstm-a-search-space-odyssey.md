## LSTM: A Search Space Odyssey
* [paper](http://cn.arxiv.org/pdf/1503.04069v1)

### LSTM overview
* [This](http://colah.github.io/posts/2015-08-Understanding-LSTMs/) is an awfully great explanation of the idea behind LSTM and its variations.

### Experiment
* Vanilla LSTM
    * ![vanilla LSTM](http://img.blog.csdn.net/20170111154914680?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
    * ![formulation of vanilla LSTM](http://img.blog.csdn.net/20170111155937348?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* Tested modifications:
    1. No Input Gate (NIG)
    2. No Forget Gate (NFG)
    3. No Output Gate (NOG)
    4. No Input Activation Function (NIAF)
    5. No Output Activation Function (NOAF)
    6. No Peepholes (NP)
    7. Coupled Input and Forget Gate (CIFG)
    8. Full Gate Recurrence (FGR)
* Hyperparameter Search
    * number of LSTM blocks per hidden layer: log-uniform
samples from [20, 200];
    * learning rate: log-uniform samples from [10−6, 10−2];
    * momentum: 1 − log-uniform samples from [0.01, 1.0];
    * standard deviation of Gaussian input noise: uniform samples from [0, 1].
* Tested datasets
    * TIMIT Speech corpus (speech recognition)
    * IAM Online Handwriting Database (OCR)
    * JSB Chorales (music modeling)
* Conclusions
    * Vanilla LSTM is good. Combine input/forget gate and remove peephole connections are worth trying.
    * Do not remove output gate or forget gate.
    * Learning rate is the most important parameter. Momentum is unimportant for LSTM. Gaussian noise on input may hurt.
    * Hyperparameters can be tuned independently.