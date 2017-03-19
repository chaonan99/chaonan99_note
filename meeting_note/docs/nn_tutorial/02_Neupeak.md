# Neupeak Introduction

* `npk-model-manip some-model shell`
* `load_dataset('dataset.py:train:remote')`
* `O.grad`

## Why DPFlow
* Multi-thread is easy
* Serve for multi-user (ImageNet)
* `npk-serve-dataset`

## Train.py
* `env`
* `opt` `clip_gradient_inplace(opt, 1)`
* `--fast-run` do initial experiments to determain which implementation of convolution is fast
    * If the network shape is fixed, this may speed up 3 times in average
* `-c` continue training

## Network profile

## Speed Test
* `PROFILE=1 ITER=50 BATCH_SIZE=1 ARGS='--input-desc`

## Distillation (Teacher- student framework)
* Teacher freeze parameter, do not train
* `O.utils.add_name_prefix_to_subgraph`

## Don't write your own layer!

## Debug
* `reshape`
* `callback_injector`
```python
def cb(x, value):
    print(value.eval())
    embed()
x = O.callback_injector(x, cb)
```

## Loop

## Column FC/RNN co-training

