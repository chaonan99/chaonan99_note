# `numpy.argsort` axis 问题

`numpy.argsort` 默认的 `axis=-1`，对最后一维排序返回顺序的index。[文档](https://docs.scipy.org/doc/numpy/reference/generated/numpy.argsort.html#)

```python
import numpy as np

a = np.arange(16)
np.random.shuffle(a)
a = a.reshape(4, 4)
a
# >>> array([[ 8, 14,  4,  5],
#            [ 7, 13,  1, 10],
#            [ 2,  3, 12,  0],
#            [11, 15,  9,  6]])

np.argsort(a)
# >>> array([[2, 3, 0, 1],
#            [2, 0, 3, 1],
#            [3, 0, 1, 2],
#            [3, 2, 0, 1]])

np.argsort(a, axis=0)
# >>> array([[2, 2, 1, 2],
#            [1, 1, 0, 0],
#            [0, 0, 3, 3],
#            [3, 3, 2, 1]])
```
