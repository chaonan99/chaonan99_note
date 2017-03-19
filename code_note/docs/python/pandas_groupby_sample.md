# Sample in each group for `df.groupby`

Refer to this (Stackoverflow question](http://stackoverflow.com/questions/36390406/pandas-sample-each-group-after-groupby)

```python
df = pd.DataFrame({'a': [1,2,3,4,5,6,7],
                   'b': [1,1,1,0,0,0,0]})
df.groupby('b').apply(lambda x: x.sample(n=1))
```