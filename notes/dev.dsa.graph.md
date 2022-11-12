---
id: c0cwsuu2pvu4r5oci5pnzun
title: Graph
desc: ''
updated: 1668216914161
created: 1667657406443
---

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