https://leetcode.com/classic/problems/count-equal-and-divisible-pairs-in-an-array/description/

```python
class Solution:
    def countPairs(self, nums: List[int], k: int) -> int:
        n, ans = len(nums), 0
        for i in range(n - 1):
            for j in range(i + 1, n):
                if nums[i] == nums[j] and (i * j) % k == 0:
                    ans += 1

        return ans
```

- **Time complexity**: $O(n^2)$.
- **Space complexity**: $O(1)$.