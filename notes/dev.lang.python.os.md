---
id: f1jdwz7kt2ygt0bg794xtqm
title: OS
desc: ''
updated: 1668238387110
created: 1668217231604
---

## 디렉토리 내의 파일 리스트 조회

```python
def get_files(directory: str) -> Iterator[str]:
    return (file for file in os.listdir(directory))
```