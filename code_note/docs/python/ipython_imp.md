# 不退出 ipython，reload module 的方法

* python2使用[`reload`](https://docs.python.org/2/library/functions.html#reload),python3使用[`imp.reload`](https://docs.python.org/3/library/imp.html)
```python
import imp
import numpy
# Some update to numpy
imp.reload(numpy)
```
* [在ipython中设置环境变量](http://ipython.readthedocs.io/en/stable/interactive/shell.html)
```shell
>>> %env foo=bar
```
