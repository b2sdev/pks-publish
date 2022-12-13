
## BST

```java
Integer last_printed = null;
boolean checkBST(TreeNode n) {
  if (n == null) return true;
  
  // 왼쪽을 재귀적으로 검사
  if (!checkBST(n.left)) return false;
  
  // 현재 노드 검사
  if (last_printed != null && n.data <= last_printed) {
    return false;
  }
  last_printed = n.data;

  // 오른쪽을 재귀적으로 검사
  if (!checkBST(n.right)) return false;

  return true; // 검사 통과
}

boolean checkBST(TreeNode n) {
  return checkBST(n, null, null);
}

// Root에서 내려가면서 해당 노드가 가질 수 있는 값을 제한
// 최솟값과 최댓값을 아래로 전달
// TC: O(N), SC: O(logN)
boolean checkBST(TreeNode n, Integer min, Integer max) {
  if (n == null) return true;

  if ((min != null && n.data <= min) || (max != null && n.data > max)) {
    return false;
  }

  // 왼쪽으로 분기하면 max를, 오른쪽으로 분기하면 min을 갱신
  if (!checkBST(n.left, min, n.data) || !checkBST(n.right, n.data, max)) {
    return false;
  }

  return true;
}


// 정렬된 배열을 BST로 만들기

void makeTree(int[] a) {
  root = makeTreeR(a, 0, a.length - 1);
}

Node makeTreeR(int[] a, int start, int end) {
  if (start > end) return null;
  int mid = (start + end) / 2;
  Node node = new Node(a[mid]);
  node.left = makeTreeR(a, start, mid - 1);
  node.right = makeTreeR(a, mid + 1, end);
  return node;
}

// 주어진 트리가 BST인지 확인

int index = 0;
void inorder(Node root, int[] array) {
  if (root != null) {
    inorder(root.left, array);
    array[index] = root.data;
    index++;
    inorder(root.right, array);
  }
}

// 순서대로 출력

void levelOrderPrint(Node root) {
  if (root == null) return;
  Queue<Node> q = new LinkedList<>();
  q.add(root);
  while (!q.isEmpty()) {
    Node n = q.poll();
    System.out.print(n.data + " ");
    if (n.left != null)
      q.add(n.left);
    if (n.right != null)
      q.add(n.right);
    }
  }
}

// 역순으로 출력

void reverseLevelOrder(Node node) {
  Stack<Node> S = new Stack();
  Queue<Node> N = new LinkedList();

  Q.add(node);

  while (!Q.isEmpty()) {
    Node n = Q.peek();
    S.push(n);

    if (n.right != null)
      Q.add(n.right);
    if (n.left != null)
      Q.add(n.left);
  }

  while (!S.empty()) {
    Node n = S.peek();
    System.out.print(n.data + " ");
    S.pop();
  }
}

// 층별로 출력

void levelOrderPrint(Node root) {
  if (root == null) return;
  Queue<Node> q = new LinkedList<>();
  q.add(root);
  q.add(null);
  while (!q.isEmpty()) {
    Node n = q.poll();
    if (n == null) {
      if (!q.isEmpty()) {
        q.add(null);
        System.out.println();
      }
    } else {
      if (n.left != null)
        q.add(n.left);
      if (n.right != null)
        q.add(n.right);
      System.out.print(n.data + " ");
    }
  }
}
```

## Binary Search Tree Interator

```java
// https://leetcode.com/problems/binary-search-tree-iterator/discuss/52525/My-solutions-in-3-languages-with-Stack

public class BSTIterator {
    private Stack<TreeNode> stack = new Stack<TreeNode>();
    
    public BSTIterator(TreeNode root) {
        pushAll(root);
    }
/** @return whether we have a next smallest number */
    public boolean hasNext() {
        return !stack.isEmpty();
    }
/** @return the next smallest number */
    public int next() {
        TreeNode tmpNode = stack.pop();
        pushAll(tmpNode.right);
        return tmpNode.val;
    }
    
    private void pushAll(TreeNode node) {
        for (; node != null; stack.push(node), node = node.left);
    }
}
```

## 트리의 높이
```java
int height(Node root) {
  if (root == null) return 0;
  int lh = height(root.left);
  int rh = height(root.right);
  if (lh > rh) return lh + 1;
  return rh + 1;
}
```