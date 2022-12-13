
## 부분 적용

```python
def filterBy(filter_fn):
    return functools.partial(filter, filter_fn)
```
@FunctionalProgramming