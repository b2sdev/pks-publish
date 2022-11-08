---
id: cazeafhpm43z9mt0yscadjg
title: Tree
desc: ''
updated: 1667656798115
created: 1667656798115
---

## 트리를 순회하는 방법은 무엇인가?

```python
# 임의의 노드에서 깊이 우선 탐색을 시작하는 것이다.

def dfs(curr, prev):
	for next in adj[curr]:
		if next != prev:
			dfs(next, curr)

dfs(x, 0) # 노드 x에서 탐색을 시작. 이전 노드가 없으므로 prev는 0.
```

## 서브트리의 노드 수

```python
# 동적 계획법
def dfs(curr, prev):
 	counts[curr] = 1
 	for next in adj[curr]:
 		if next == prev:
 			continue
 		dfs(next, curr)
 		counts[curr] += count[next]
```
#DynamicProgramming

