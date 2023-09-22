---
id: s66kv1tn9vjsl1sybm55rvv
title: 소인수분해 후 각 소인수의 지수의 합 구하기
desc: ''
updated: 1695369529094
created: 1695368030735
---

## 문제
$1 \times 2 \times 3 \times ··· \times 10$을 소인수분해하면 $2^x \times 3^y \times 5^z \times 7$이다. 이때 자연수 $x, y, z$에 대하여 $x+y+z$의 값을 구하시오.

## 풀이
주어진 수를 소인수분해 후 각 소인수의 지수를 모두 합산한다.

```python
from collections import Counter

num = 1
for n in range(2, 11):
    num *= n

factors = Counter(prime_factorization(num))

x = factors[2]
y = factors[3]
z = factors[5]

print(x + y + z)
```

소인수분해 코드는 아래를 참고한다.
![[dev.dsa.math.prime_factorization]]

## References
문제 0131, 쎈 중등 수학 1-1, (주)좋은책신사고