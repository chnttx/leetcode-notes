https://leetcode.com/classic/problems/maximum-candies-allocated-to-k-children/description/

### Intuition

- Similar to Koko Eating Bananas, for `c` candies, we need to check if each child can get `c` candies.
- Use binary search to find the maximum `c`.

```python
class Solution:
    def _helper(self, candies: List[int], c: int, k: int) -> bool:
        max_children = 0
        for pile in candies:
            max_children += pile // c

        return max_children >= k
    
    def maximumCandies(self, candies: List[int], k: int) -> int:
        _min, _max = 0, max(candies)

        while _min < _max:
            middle = (_min + _max + 1) // 2
            if self._helper(candies, middle, k):
                _min = middle
            else:
                _max = middle - 1

        return _min
```

- **Time complexity**: $O(nlogm)$.
- **Space complexity**: $O(1)$.