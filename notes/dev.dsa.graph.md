---
id: c0cwsuu2pvu4r5oci5pnzun
title: Graph
desc: ''
updated: 1668242780977
created: 1542634080000
---

## What

```
개체들 사이의 일대일 관계를 시각적으로 표현하는 수학적 모델
그래프는 vertex(꼭지점, 정점)와 edge(간선)의 집합
G = (V, E)
	V: Vertex는 개체를 나타냄
	E: Edge는 일대일 관계를 나타냄
	   Edge는 vertex의 쌍으로 표현됨
그래프의 수학적/시각적 표현
	V = {0, 1, 2, 3}
	E = {(0,2), (0,3), (1,2), (1,3)))}
Edge 리스트를 이용한 표현
	4, 4 // vertex의 수, edge의 수
	0, 2
	0, 3
	1, 2
	1, 3
	
용어
vertex
하나의 개체를 표현
edge
vertex와 verte의 1:1 관계 -> (0, 1)
path
cycle
첫 번째 vertex와 마지막 vertex가 일치하는 단순 경로
connected acylic graph = tree
```

## 그래프 탐색
- 깊이 우선 탐색
  - 재귀-간단
  - 다른 인접 노드를 방문하기 전에 특정한 인접 노드를 깊이 있게 탐색
- 너비 우선 탐색
  - 최단 경로

## Graph with adjacent list and DFS

```java
import java.util.LinkedList;
import java.util.Stack;

public class Graph {
  LinkedList<Interger>[] vertex;

  public Graph(int size) {
    this.vertex = vertex;
    vertex = new LinkedList[size];
    for (int i = 0; i < vertex; i++) {
      vertex[i] = new LinkedList<>();
    }
  }

  public void addEdge(int source, int destination) {
    vertex[source].addFirst(destination);
  }

  public void DFS() {
    System.out.print("Depth First Traversal: ");
    boolean[] visited = new boolean[vertex.length];
    Stack<Integer> stack = new Stack<>();

    for (int startIndex = 0; startIndex < vertex; startIndex++) {
      if (visited[startIndex] == false) {
        stack.push(startIndex);
        visited[startIndex] = true;
        while (stack.isEmpty() == false) {
          int nodeIndex = stack.pop();
          System.out.print(nodeIndex + " ");
          LinkedList<Integer> adjacent = vertex[nodeIndex];
          for (int i = 0; i < adjacent.size(); i++) {
            int dest = adjacent.get(i);
            if (visited[dest] == false) {
              stack.push(dest);
              visited[dest] = true;
            }
          }
        }
      }
    }
    System.out.println();
  }

  public static void main(String[] args) {
    Graph graph = new Graph(6);
    graph.addEdge(0, 1);
    graph.addEdge(0, 2);
    graph.addEdge(1, 2);
    graph.addEdge(1, 3);
    graph.addEdge(3, 4);
    graph.addEdge(2, 3);
    graph.addEdge(4, 0);
    graph.addEdge(4, 1);
    graph.addEdge(4, 5);
    graph.printGraph();
    graph.DFS();
  }
}
```