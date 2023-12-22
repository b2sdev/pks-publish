
## 문제
60보다 작은 자연수 _k_의 약수의 개수가 4일 때, _k_가 될 수 있는 수의 개수는?

## 풀이
- 60보다 작은 모든 자연수의 소인수분해의 결과를 `Counter`를 사용하여 **각 소수의 개수**를 구한다.
- 소수의 개수가 `약수의 개수가 4`라는 조건에 부합하면 count를 추가한다.
    - 어떤 자연수의 **약수의 개수가 4**가 되려면, 그 자연수는 **_소인수 하나의 세제곱_**(조건1) 또는 **_소인수 두 개의 곱_**(조건2)의 꼴이어야 한다.

```python
from collections import Counter

def solution() {
    def cond1(factors):
        if len(factors) == 1:
            if list(factors.values())[0] == 3:
                return True
        return False
    def cond2(factors):
        if len(factors) == 2:
            if sum(list(factors.values())) == 2:
                return True
        return False

    count = 0
    for k in range(1, 60):
        factors = Counter(prime_factorization(k))
        if cond1(factors) or cond2(factors):
          count += 1
    
    print(count)
}
```

소인수분해 코드는 아래를 참고한다.
![[dev.dsa.math.prime_factorization]]

## References
문제 0127, 쎈 중등 수학 1-1, (주)좋은책신사고