
## 디렉토리 내의 파일 리스트 조회

```python
def get_files(directory: str) -> Iterator[str]:
    return (file for file in os.listdir(directory))
```