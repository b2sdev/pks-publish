

## 다익스트라 알고리즘의 수도코드

```python
function Dijkstra(Graph, soure):
	dist[source] ← 0
	
	create vertex priority queue Q
	
	for each vertext v in Graph:
		if v ≠ source
			dist[v] ← INFINITY
			prev[v] ← UNDEFINED
		
		Q.add_with_priority(v, dist[v])
		
	while Q is not empty:
		u ← Q.extract_min()
		for each neighbor v of u:
			alt ← dist[u] + length(u, v)
			if alt < dist[v]
				dist[v] ← alt
				prev[v] ← u
				Q.decrease_priority(v, alt)
				
	return dist, prev
```

## 다익스트라 알고리즘 구현 (Python)

```python
# 그래프 인접 리스트 구성
graph = collections.defaultdict(list)
for u, v, w in info:
	graph[u].append((v, w))

# 큐 변수: [(거리, 정점)]
Q = [(0, K)]
# 최단 거리 변수
dist = collections.defaultdict(int)

# 우선순위 큐 최솟값 기준으로 정점까지 최단 경로 삽입
while Q:
	d, u = heapq.heappop()
	if node not in dist:
		dist[u] = d
		for v, w in graph[u]:
			alt = d + w
			heapq.heappush(Q, (alt, v))	
```

## 다익스트라 알고리즘 구현 (Java)

```java
int[] dijkstra(Graph G, int s) {
  final int[] dist = new int[G.size()];
  final int[] pred = new int[G.size()];
  for (int i=0; i<dist.length; i++) {
    dist[i] = Integer.MAX_VALUE;
    pred[i] = false;
  }

  final boolean[] visited = new boolean[G.size()];

  dist[s] = 0;

  for (int i=0; i<dist.length; i++) {
    final int u = extractMin(dist, visited);
    visited[u] = true;
    final int[] n = G.neighbors(u);
    for (int j=0; j<n.length; j++) {
      final int d =  dist[u] + G.weight(u, v);
      if (dist[v] > d) {
        dist[v] = d;
        pred[v] = u;
      }
    }
  }

  return pred;
}
```