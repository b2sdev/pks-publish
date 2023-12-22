
소수(prime number)는 **에라토스테네스의 체** 알고리즘으로 구한다.

```python
def sieve_of_eratosthenes(n):
    """Return a list of all prime numbers less than n."""
    sieve = [True] * n
    sieve[0], sieve[1] = False, False  # 0과 1은 소수가 아니다.
    
    for i in range(2, int(n ** 0.5) + 1):
        if sieve[i]:
            for j in range(i*i, n, i):
                sieve[j] = False  # i의 배수는 모두 소수가 아니다.

    return [i for i, is_prime in enumerate(sieve) if is_prime]

num = 30
print(sieve_of_eratosthenes(num))  # [2, 3, 5, 7, 11, 13, 17, 19, 23, 29] 출력
```