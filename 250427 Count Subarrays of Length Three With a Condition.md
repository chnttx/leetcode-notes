https://leetcode.com/classic/problems/count-subarrays-of-length-three-with-a-condition/

```python
class Solution:
    def countSubarrays(self, nums: List[int]) -> int:
        left, mid, right, n = 0, 1, 2, len(nums)
        ans = 0
        while right < n:
            ans = ans + 1 if (nums[left] + nums[right]) * 2 == nums[mid] else ans
            left += 1
            mid += 1
            right += 1
        return ans
```

- **Time complexity**: $O(n)$.
- **Space complexity**: $O(1)$.