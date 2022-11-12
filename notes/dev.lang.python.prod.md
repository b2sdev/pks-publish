---
id: fiz4kqdcmvllh0152ftb82s
title: Math
desc: ''
updated: 1668238414769
created: 1667046443331
---

`math.prod` is a new function (from Python 3.8).

```python
import math

numbers = [1, 2, 3, 4]

print(math.prod(numbers))
```

If you want to have a more compatible code, you should use the old way:

```python
from functools import reduce
import operator

print(reduce(operator.mul, [1,2,3,4], 1))
```