https://leetcode.com/problems/find-minimum-operations-to-make-all-elements-divisible-by-three

### Intuition
- we just to have to calculate the distance between `nums[i]` and the nearest multiple of 3

```python
class Solution:
    def minimumOperations(self, nums: List[int]) -> int:
        # greedy approach
        # move element to nearest multiple of 3
        ans = 0
        for n in nums:
            m = n % 3
            ans += min(3 - m, m)

        return ans
```

- **Time complexity**:$O(n)$.
- **Space complexity**: $O(1)$.