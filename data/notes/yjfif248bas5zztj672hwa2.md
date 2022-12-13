
```python
# https://leetcode.com/problems/number-of-enclaves/

def numEnclaves(self, grid: List[List[int]]) -> int:
  """
  경계에 있는 cell이 1인 넘과 그넘 친구들을 0으로 변환 후,
  grid에 남아있는 cell의 개수를 카운트한다.
  """
  def out_of_grid(r, c):
    return r < 0 or r >= len(grid) or c < 0 or c >= len(grid[0])

  def dfs(r, c):
    if out_of_grid(r, c):
      return

    if grid[r][c] != 1:
      return

    grid[r][c] = 0

    direction = (0, 1)
    for _ in range(4):
      direction = (direction[1], -direction[0])
      nr, nc = r + direction[0], c + direction[1]
      dfs(nr, nc)

  m, n = len(grid), len(grid[0])
  ans = 0
  for r in range(m):
    dfs(r, 0)
    dfs(r, n - 1)
  for c in range(n):
    dfs(0, c)
    dfs(m - 1, c)

  return sum([sum(row) for row in grid])
```