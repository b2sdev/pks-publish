---
id: ktsjn4s21wagp62qtp6oq94
title: Python으로 file 다루기
desc: ''
updated: 1669269827683
created: 1669269639581
---

## Text file 읽기

```python
with open('file.txt', encoding='utf8') as f:
    for lines in f:
        print(line.strip())
```

## References
- https://pythontutorial.net/python-basics/python-read-text-file/