---
id: 6ge8dy2vkiqpcncw11db5nz
title: Codility
desc: ''
updated: 1667827431184
created: 1667827431184
---

## Lesson 1 Iterations

### BinaryGap
```python
def solution(N):
	gaps = list(map(len, format(N, 'b')))
	if N % 2 == 0:
		gaps = gaps[:-1]
	return max(gaps)
```

## Lesson 2 Arrays

### CyclicRotation
```python
def solution(A, K):
	k = K % len(A) if len(A) > 0 else K
	return A[len(A) -k:] + A[:len(A) - k]
```