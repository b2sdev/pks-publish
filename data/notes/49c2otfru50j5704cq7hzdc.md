
```python
import collections

dp = collections.defaultdict(int)

# Recursive
def fib(N):
    if N <= 1:
        return N

    if dp[N]:
        return dp[N]

    dp[N] = fib(N - 1) + fib(N - 2)
    return dp[N]

# Bottom-up
def fibo(N):
    dp[1] = 1

    for i in range(2, N + 1):
        dp[i] = dp[i - 1] + dp[i - 2]

    return dp[N]

def fibonacci(N):
    x, y = 0, 1
    for i in range(0, N):
        x, y = y, x + y
    return x 
```

#DynamicProgramming