---
id: yczd3hv0634qxe3j6fe7q55
title: Functools
desc: ''
updated: 1668217197033
created: 1668217120569
---

## 부분 적용

```python
def filterBy(filter_fn):
    return functools.partial(filter, filter_fn)
```
@FunctionalProgramming