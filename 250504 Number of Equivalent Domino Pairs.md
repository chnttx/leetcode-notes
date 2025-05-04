https://leetcode.com/classic/problems/number-of-equivalent-domino-pairs/description/

```python
class Solution:
    def numEquivDominoPairs(self, dominoes: List[List[int]]) -> int:
        n = len(dominoes)
        seen = Counter()
        ans = 0
        for domino in dominoes:
            a, b = min(domino), max(domino)
            ans += seen.get((a, b), 0)
            seen[tuple([a, b])] += 1
        return ans
```

- **Time complexity**: $O(n)$.
- **Space complexity**: $O(n)$.