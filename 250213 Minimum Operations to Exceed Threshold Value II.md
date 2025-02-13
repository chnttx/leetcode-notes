https://leetcode.com/problems/minimum-operations-to-exceed-threshold-value-ii

#priority-queue #greedy

## Approach

- In each operation, we have to extract 2 smallest values => use heap to maintain smallest number at top of queue

```python
class Solution:
    def minOperations(self, nums: List[int], k: int) -> int:
        heapq.heapify(nums)
        ans = 0
        while len(nums) > 1 and nums[0] < k:
            x = heapq.heappop(nums)
            y = heapq.heappop(nums)
            heapq.heappush(nums, min(x, y) * 2 + max(x, y))
            ans += 1

        return ans
```

- **Time complexity**: $O(nlogn)$
- **Space complexity**: $O(1)$, since `heapq.heapify` is in-place