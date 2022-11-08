---
id: 6qoeufgmgbzekihukmsdqe5
title: Binary Tree
desc: ''
updated: 1667656985620
created: 1667656985620
---

## 이진 트리의 최대 깊이

```python
def maxDepth(root):
    if root is None:
        return 0

    queue = collections.deque([root])
    depth = 0

    while queue:
        depth += 1
        # 큐 연산 추출 노드의 자식 노드 삽입
        for _ in range(len(queue)):
            cur_root = queue.popleft()
            if cur_root.left:
                queue.append(cur_root.left)
            if cur_root.right:
                queue.append(cur_root.right)

    # BFS 반복 횟수 == 깊이
    return depth
```

## 이진 트리의 지름

```python
def diameterOfBinaryTree(root):
    def dfs(node):
        nonlocal diameter

        if not node:
            return 0

        left = dfs(node.left)
        right = dfs(node.right)

        diameter = max(diameter, left + right)

        return max(left, right) + 1

    diameter = 0
    dfs(root)
    return diameter
```

## 이진 트리의 높이

```python
def height(root):
 	if root is None:
		return 0
	return 1 + max(height(root.left), height(root.right)
	
def height(root):
	if not root: return 0
	h = 0
	queue = collections.deque([root])
	while queue:
		for _ in range(len(queue)):
			curr_node = queue.popleft()
			if curr_node.left:
				queue.append(curr_node.left)
			if curr_node.right:
				queue.append(curr_node.right)
		h += 1
	return h
```

### 이진 트리의 최소 깊이

```python
def minDepth(root):
	if not root:
		return 0
	if root.left and root.right:
		return min(minDepth(root.left), minDpeth(root.right)) + 1
	else:
		return minDepth(root.left or root.right) + 1 def minDepth(root):
 	queue = collections.dqeue((root, 1))
 	while queue:
 		node, level = queue.popleft()
 		if node:
 			if not node.left and not node.right:
 				return level
 			else:
 				queue.append((node.left, level + 1))
 				queue.append((node.right, level + 1))
```

## 이진 트리 순회
- 전위(Pre-order) 순회: NLR
- 중위(In-order) 순회: LNR
- 후위(Post-order) 순회: LRN
- Recursion
```python
def preorder(node):
	if node is None:
		return
	print(node.val)
	preorder(node.left)
	preorder(node.right)
	
def inorder(node):
	if node is None:
		return
	inorder(node.left)
	print(node.val)
	inorder(node.right)
	
def postorder(node):
	if node is None:
		return
	postorder(node.left)
	postorder(node.right)
	postorder(node.val)
```
- Iterative
```python
def traverse_preorder(root):
    if not root:
        return

    stack = [root]

    while stack:
        node = stack.pop()
        print(node.val, end=" ")
        if node.right:
            stack.append(node.right)
        if node.left:
            stack.append(node.left) def traverse_inorder(root):
    stack = []
    node = root
    while stack or node:
        while node:
            stack.append(node)
            node = node.left

        node = stack.pop()

        print(node.val, end=" ")

        node = node.right
```
```python
# https://www.geeksforgeeks.org/iterative-postorder-traversal-using-stack/

def postOrderIterative(root):
    node = root
    stack = []
    while True:
        while node:
            stack.append(node)
            stack.append(node)
            node = node.left

        if not stack:
            break

        node = stack.pop()

        # 현재 노드의 첫번째 방문일때, 오른쪽으로 이동
        if stack and stack[-1] == node:
            node = node.right
        # 현재 노드를 두번째 방문 했을때 출력한다.
        else:
            print("visited", node.val)
            node = None  # The first is by postorder using a flag to indicate whether the node has been visited or not.
def postOrderTraversal(root): 	
 	traversal, stack = [], [(root, False)]
 	while stack:
 		node, visited = stack.pop()
 		if node:
 			if visited:
 				# add to result if visited
 				traversal.append(node.val)
 			else:
 				# post-order
 				stack.append((node, True))
 				stack.append((node.right, False))
 				stack.append((node.left, False))
 	
 	return traversal
 
 
# The 2nd uses modified preorder (right subtree first). Then reverse the result.

def postorderTraversal(root):
	traversal, stack = [], [root]
	while stack:
		node = stack.pop()
		if node:
			# pre-order, right-first
			traversal.append(node.val)
			stack.append(node.left)
			stack.append(node.right)
	
	# reverse result
	return traversal[::-1]
```