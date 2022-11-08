---
id: zptf7g0kt1w9wji3ewgmbv9
title: Number of Islands
desc: ''
updated: 1667657557410
created: 1667657557410
---

```python
# https://leetcode.com/problems/number-of-islands/

def numIslands(self, grid) -> int:
  def out_of_grid(r, c):
    return r < 0 or r >= len(grid) or c < 0 or c >= len(grid[0])

  def dfs(r, c):
    if grid[r][c] != "1":
      return

    grid[r][c] = 0"

    direction = (0, 1)
    for _ in range(4):
      direction = (direction[1], -direction[0])
      nr, nc = r + direction[0], c + direction[1]
      if not out_of_grid(nr, nc):
        dfs(nr, nc)

  ans = 0
  for r in range(len(grid)):
    for c in range(len(grid[0])):
      if grid[r][c] == "1":
        dfs(r, c)
        ans += 1

  return ans
```