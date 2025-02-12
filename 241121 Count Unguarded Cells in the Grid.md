https://leetcode.com/problems/count-unguarded-cells-in-the-grid/

### Approach

- Run 1-directional dfs on each guard for each direction until they run into a guarded cell/guard/wall

```python
class Solution:
    def countUnguarded(self, m: int, n: int, guards: List[List[int]], walls: List[List[int]]) -> int:
        guarded = set()
        walls = set(list(map(tuple, walls)))
        guards = set(list(map(tuple, guards)))
        
        directions = [(-1, 0), (0, -1), (1, 0), (0, 1)]
        
        # 1-directional DFS until out of bounds or collision
        def dfs(x: int, y: int, dx: int, dy: int) -> None:
            nx, ny = x + dx, y + dy
            # Out of bounds
            if nx < 0 or ny < 0 or nx >= m or ny >= n:
                return
            
            # Occupied by guard/wall
            if (nx, ny) in walls or (nx, ny) in guards:
                return
            
            guarded.add((nx, ny))
            dfs(nx, ny, dx, dy)
        
        for gx, gy in guards:
            for dx, dy in directions:
                dfs(gx, gy, dx, dy)
        
        return m * n - len(guarded) - len(guards) - len(walls)
```

- **Time complexity:** $O(g*(m + n))$, each guard has max vision of $m+n$ blocks
- **Space complexity:** $O(g*(m+n))$, `dfs` is called $m+n$ times for each guard