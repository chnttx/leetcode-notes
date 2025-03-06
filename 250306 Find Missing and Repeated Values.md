https://leetcode.com/problems/find-missing-and-repeated-values/
## Intuition

- In an ideal world, each integer in range `[1, n^2]` appears exactly once, so the sum would be $n * (n + 1) / 2$. We can use this to find the missing number by calculating the sum of all numbers that appear exactly once (including repeated's first occurence), and find the number by $sum(1, n^2) - distinctsum$

```python
class Solution:
    def findMissingAndRepeatedValues(self, grid: List[List[int]]) -> List[int]:
        repeat, missing, n = -1, -1, len(grid)
        _sum = n**2 * (n**2 + 1) // 2
        seen, curr = set(), 0
        for i in range(n):
            for j in range(n):
                if grid[i][j] in seen:
                    repeat = grid[i][j]
                else:
                    seen.add(grid[i][j])
                    curr += grid[i][j]

        missing = _sum - curr
        return [repeat, missing]
```

- **Time complexity**: $O(n^2)$
- **Space complexity**: $O(n^2)$
