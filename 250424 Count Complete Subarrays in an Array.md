https://leetcode.com/problems/count-complete-subarrays-in-an-array/description

```python
class Solution:
    def countCompleteSubarrays(self, nums: List[int]) -> int:
        # Maintain window, if we find a complete subarray then any subarray [l:r + 1 -> n] is also complete
        num_distinct = len(set(nums))
        l, r, n, ans = 0, 0, len(nums), 0
        window = Counter()
        while r < n:
            window[nums[r]] += 1
            while len(window) == num_distinct:
                ans += n - r
                window[nums[l]] -= 1
                if window[nums[l]] == 0:
                    window.pop(nums[l])
                l += 1
            r += 1

        return ans
```

- **Time complexity**: $O(n)$.
- **Space complexity**: $O(n)$.