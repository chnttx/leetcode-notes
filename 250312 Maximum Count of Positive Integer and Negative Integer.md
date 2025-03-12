https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/description

```python
class Solution:
    def maximumCount(self, nums: List[int]) -> int:
        neg, pos = 0, 0
        for n in nums:
            if n < 0:
                neg += 1
            elif n > 0:
                pos += 1

        return max(neg, pos)
```

- **Time complexity**: $O(n)$.
- **Space complexity**: $O(1)$.