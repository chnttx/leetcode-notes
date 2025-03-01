https://leetcode.com/problems/apply-operations-to-an-array/

```python
class Solution:
    def applyOperations(self, nums: List[int]) -> List[int]:
        n = len(nums)
        for i in range(n - 1):
            if nums[i] == nums[i + 1]:
                nums[i] *= 2
                nums[i + 1] = 0

        ans = [m for m in nums if m]
        return ans + [0] * (n - len(ans))
```

- **Time complexity**: $O(n)$
- **Space complexity**: $O(n)$