
From docs python, under heapq.heappop definition, it says:

**To access the smallest item without popping it, use heap[0].**

It says smallest, because it is a min heap. So the item at the top will be the smallest one.

```python
import heapq

pq = []

heapq.heappush(pq,5)
heapq.heappush(pq,3)
heapq.heappush(pq,1)
heapq.heappush(pq,2)
heapq.heappush(pq,4)

print("element at top = ",pq[0])
print("check the heapq : ", pq)
```

Result
```python
element at top =  1
check the heapq :  [1, 2, 3, 5, 4]
```

### References
- https://stackoverflow.com/questions/64246136/how-to-access-the-top-element-in-heapq-without-deleting-popping-it-python