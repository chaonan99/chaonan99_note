## Recurrent Models of Visual Attention
[paper link](https://arxiv.org/pdf/1406.6247v1.pdf)
> Tutorial and torch implementation [here](http://torch.ch/blog/2015/09/21/rmva.html).

![2016_08_29_18679d6f77d194f7a9030548b12133b](http://oa5omjl18.bkt.clouddn.com/2016_08_29_18679d6f77d194f7a9030548b12133b.png "Model of this paper")

### Highlights
1. They use [reinforcement learning](https://www.nervanasys.com/demystifying-deep-reinforcement-learning/) on part of the network.
2. Their visual attention is to extract a series of bandlimited sub-images, concretely, use the same center and different sizes to get sub-images and scale them to the same size.

### Reinforce training method
In their model, they generate location for glimpse in each time step. They are assuming that the location is sampled from a normal distribution parameterized by ![img](http://latex.codecogs.com/svg.latex?%5Cmu) and ![img](http://latex.codecogs.com/svg.latex?%5Csigma). They make ![img](http://latex.codecogs.com/svg.latex?%5Csigma) to be fixed (thus hold a fixed attention band width), and try to learn propriate ![img](http://latex.codecogs.com/svg.latex?%5Cmu), which is the average glimpse location (detailed formulations are shown in the blog post above). Only the last time step and the predicted class is correct will give R=1. In other cases, R=0.

### Not finished
* Haven't seen the experiment result yet.