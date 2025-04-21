https://leetcode.com/classic/problems/count-the-hidden-sequences/description/

## Intuition

- We can think of `differences` as fluctuations, where the global minimum would be where `lower` is and global maximum would be where `upper` is.
- Use prefix sum for this

```python
class Solution:
    def numberOfArrays(self, differences: List[int], lower: int, upper: int) -> int:
        # Use prefix sum, min would be where lower is, max would be where upper is
        prefix_sum = [0]
        for diff in differences:
            prefix_sum.append(prefix_sum[-1] + diff)
        _min, _max = min(prefix_sum), max(prefix_sum)
        return max(upper - lower + 1 - (_max - _min), 0) # in case there are no valid sequences
```

- **Time complexity:** $O(n$).
- **Space complexity:** $O(n)$.