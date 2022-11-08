---
id: 4docp4jbbgo25mtbarxp0av
title: Sief (TBD)
desc: ''
updated: 1667042478830
created: 1667042478831
---

```python
# 소수가 아닌 수를 지워가는 과정
# def mark_sieve(first, last, factor):
#   *first = False
#   while last - first > factor:
#     first = first + factor
#     *first = False


def sief0(n):
  sieve = [0] * (n + 1)
  
  for x in range(2, n + 1):
    if sieve[x]: continue
    for u in range(2*x, n + 1, x):
      sieve[u] = 1

  print(sieve[2:])

def sief1(n):
  def mark_sieve(first, last, factor):
    sieve[first] = False
    while last - first > factor:
      first = first + factor
      sieve[first] = False

  sieve = [True] * (n + 1)
  for x in range(2, n + 1):
    # if sieve[x]: continue
    mark_sieve(x, n + 1, x)
  print(sieve[2:])

sief0(10)
sief1(10)
```