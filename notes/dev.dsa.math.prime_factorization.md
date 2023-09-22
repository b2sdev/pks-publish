---
id: 5md3q9daagijj4py0g1avkb
title: 소인수분해
desc: ''
updated: 1695369405219
created: 1695365191314
---

```python
def prime_factorization(n):
    """Return the prime factorization of a number."""
    factors = []
    divisor = 2  # 시작하는 소수

    while divisor <= n:
        if n % divisor == 0:  # n이 divisor로 나누어 떨어지면
            factors.append(divisor)
            n //= divisor   # n을 divisor로 나눈 몫을 새로운 n으로 설정
        else:
            divisor += 1

    return factors

num = 56
print(prime_factorization(num))  # [2, 2, 2, 7] 출력
```