https://leetcode.com/classic/problems/alternating-groups-ii/

## Intuition

- Because the problem asks for `every k contiguous tiles`, the optimal solution would be to maintain a fixed #sliding-window of size `k`  and keep track of which window fits the criteria.
- This would have a time complexity of $O(k*n)$. We only have to consider tiles right before current tile, so maintaining `prev` saves time of checking each window.
- If `colors[right] == prev`, reset start of window to `right` .

```python
class Solution:
    def numberOfAlternatingGroups(self, colors: List[int], k: int) -> int:
        left, right = -k + 1, -k + 1
        n = len(colors)
        prev = -1 # there's no previous to consider yet
        ans = 0
        while right < n:
            if colors[right] == prev:
                left = right
                
            prev = colors[right]

            if right - left + 1 == k:
                ans += 1
                left += 1

            right += 1
        
        return ans
```

- **Time complexity**: $O(n + k)$.
- **Space complexity**: $O(1)$.
