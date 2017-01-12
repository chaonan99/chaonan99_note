## Microsoft Video Description Corpus (MSVD)
* [dataset link](https://www.microsoft.com/en-us/download/details.aspx?id=52422)
* [dataset paper link](http://www.cs.utexas.edu/~ml/papers/chen.acl11.pdf)

### Description
This data consists of about 120K sentences collected during the summer of 2010. Workers on Mechanical Turk were paid to watch a short video snippet and then summarize the action in a single sentence. The result is a set of roughly parallel descriptions of more than 2,000 video snippets. Because the workers were urged to complete the task in the language of their choice, both paraphrase and bilingual alternations are captured in the data. We expect this data to be useful for training and testing translation and paraphrase algorithms. A paper describing how the data was created and used is in progress.

### Scale
1970 clips (train/validate/test:1200/100/670), 80k clip-description pairs (**multi-language**), have **audio**.

### Duration
Usually less than 10 seconds.

### Examples

[![2016_09_01_227420e81de92e12b54e9aed867253](http://oa5omjl18.bkt.clouddn.com/2016_09_01_227420e81de92e12b54e9aed867253.png "Add Description")](https://youtu.be/mv89psg6zh4?t=33s)

* Ground truth:
    + A bird in a sink keeps getting under the running water from a faucet.
    + A bird is bathing in a sink.
    + A bird is splashing around under a running faucet.
    + A bird is bathing in a sink.
    + A bird is standing in a sink drinking water that is pouring out of the facet.
    + A faucet is running while a bird stands in the sink below.
    + ......(many others)

* Some other video:
    + [A man is riding a motorcycle.](https://youtu.be/msCidKHOh74?t=6m50s)
    + [The man jumped on the wall.](https://youtu.be/ItFqogTmAvQ?t=48s)
    + [A man is playing pat-a-cake with a small black dog.](https://youtu.be/eyhzdC936uk?t=15s)

### Papers using the dataset
* [Hierarchical Recurrent Neural Encoder for Video Representation with Application to Captioning](hierarchical-recurrent-neural-encoder-for-video-representation-with-application-to-captioning.md)
* [Describing Videos by Exploiting Temporal Structure](describing-videos-by-exploiting-temporal-structure.md)
