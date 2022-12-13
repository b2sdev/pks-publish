

```python
def gcd(a, b):
    while b != 0:
        a = a % b
        a, b = b, a
    return a

print(gcd(30, 6)) # 6
print(gcd(6, 30)) # 6
```