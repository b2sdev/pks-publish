---
id: edz7dtpw37iqg7uejfq1x7g
title: Problem Solving Tips
desc: ''
updated: 1667826750626
created: 1667826750626
---

## 입력 처리
```python
# 다음을 고할 것
# 숫자인지, 문자인지
# 음수
# 정수 여부
# 정렬 여부
# 입력 값이 없는 경우
# 입력 리스트 내부를 직접 조작해도 되는지 ~ immutable
# 대소문자 구분

if not strs:
if len(s) < 2:
if s == s[::-1]
```

## 리스트 초기화
```python
answer = [0] * len(in)
```

## 최댓값/최솟값
```python
mx = -sys.maxsize
mn = sys.maxsize

mx = float('-inf')
mn = float('inf')
```

## 문자
```python
char.isalnum()
char.lower()
char.isdigit()
char.isnumeric()

# isdecimal() ⊆ isdigit() ⊆ isnumeric()
# https://stackoverflow.com/questions/44891070/whats-the-difference-between-str-isdigit-isnumeric-and-isdecimal-in-python
```

## 문자열
```python
strs.lower()
strs.reverse() ~ strs[:] = strs[::-1]
```

## Matrix
```python
any(target in row for row in matrix)
```

## 정규식
```python
import re

s = re.sub('[^a-z0-9]', '', s)
word = re.sub(r'[^\w]', ' ', paragraph)
```

## Counter
```python
import collections

counts = collections.Counter(words)

return counts.most_common(1)[0][0]
또는 sorted(counts.items(), key=lambda x: x[1])
```

## List ~ 문자열
```python
strs.pop(0)  # O(n)
strs.pop()

lst.index(val)

max(lst, key=len)

result = int(''.join(str(e) for e in a))
result = int(''.join(map(str, a))

next_elements = elements[:] # 값을 참조가 아닌 복사
next_elements.remove(e)

path + [candidates[i]]

new_list = [12, 3].copy
```

## Deque
```python
import collections

strs: Deque = collections.deque()
strs.popleft()  # O(1)
```

## Two pointers
```python
left, right = 0, len(s) - 1
while left < right:
  # do something
  s[left], s[right] = s[right], s[left]
  left += 1
  right -= 1

# 06 longest palindromic substring
# 08 trapping rain water
# 09 3sum
# 30 longest-substring-without-repeating-characters
# 63 sort-colors
# 67 intersection-of-two-arrays
# 76 minimum-window-substring

# Runner
slow = fast = head
while fast and fast.next:
  fast = fast.next.next
  slow = slow.next

# 13 palindrome-linked-list
# 58 sort-list
```

## 정렬
```python
s.sort(key=lambda x: (x.split()[1], x.split()[0]))
s.sort(key=lambda x: (x.split()[1:], x.split()[0]))

''.join(sorted(s))
```

## Dict
 
collections.defaultdict(int)
collections.defaultdict(list)

## 예외 처리
- stack에서 pop 전에 stack이 비었는지 확인
  if not stack or table[char] != stack.pop(): return False


## Stack
```python
stack = []
top = stack[-1]

stack = collections.deque([root])
while stack:
  node = stack.pop()
  if node:
    ...
```

## Queue
```python
queue = collections.deque([root])
while queue:
  node = queue.popleft()
  if node:
    ...
```

## 우선순위 큐
```python
import heapq

heap = []
for lst in lists:
  heapq.heappush(heap, (lst.val, lst))

while heap:
  elem = heapq.heappop(heap)

freqs = collections.Counter(nums)
freqs_heap = []

for f in freqs:
  heapq.heappush(freqs_heap, (-freqs[f], f))

topk = []
for _ in range(k):
  topk.append(heapq.heappop(freqs_heap)[1])

list(zip(*collections.Counter(nums).most_common(k)))[0]
```

## 해시 테이블
```python
freqs = {}
freqs[char] += 1
if char in freqs:
  count += freqs[char]

freqs = collections.defaultdict(int)

freqs = collections.Counter(S)
```

## Set
```python
s = set()
s.add(val)
if sth in s:
```

## Sliding Window

06 longest-palindromic-substring
30 longest-substring-without-repeating-characters


## 백트래킹
```python
results = []
def dfs(index, path):
  # 끝까지 탐색하면 백트래킹
  if len(path) == len(digits):
    results.append(path)
    return

  for i in range(index, len(digits)):
    for j ...
      dfs(i + 1, path + j)
    
# 33 letter-combination-of-a-phone-number
# 34 permutations
# 35 combinations
# 44 longest-univalue-path
# 45 invert-binary-tree
# 46 merge-two-binary-trees
```

## 그래프
```python
graph = collections.defaultdict(list)
for a, b in sorted(tickets):
  graph[a].append(b)
```

## 최단 거리

## 트리
```python
mid = len(nums) // 2
node = TreeNode(nums[mid])
left = bst(nums[:mid])
right = bst(nums[mid + 1:])
```

## 분할 정복
50 convert-sorted-array-to-binary-search-tree
54 construct-binary-tree
58 sort-list

## Set
```python
result = set()
result.add(a)
```