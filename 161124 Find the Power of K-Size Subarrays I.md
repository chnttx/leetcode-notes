https://leetcode.com/problems/find-the-power-of-k-size-subarrays-i/
### Brute-force approach 

- Iterate through all k-windows

```python
class Solution:
    def resultsArray(self, nums: List[int], k: int) -> List[int]:
	    # Check if each subarray is consecutive, if not return -1, else return 
		# final element in subarray
        def findMaxInSubarray(idx: int) -> int:
            curr = nums[idx]
            for i in range(1, k):
                if nums[idx + i] - curr != 1:
                    return -1
                curr = nums[idx + i]
            return curr
        
        n = len(nums)
        ans = [0] * (n - k + 1)
		# Iterate through all k-subarrays
        for i in range(n - k + 1):
            ans[i] = findMaxInSubarray(i)
            
        return ans
```

- **Time complexity**: $O(k*n)$
- **Space complexity**: $O(n)$

### Optimized approach

- sliding window, keeping track of current number and last element of previous k-window, except edge case when k is 1

```python
class Solution:
    def resultsArray(self, nums: List[int], k: int) -> List[int]:
        
        # Edge case for singletons, since you don't need to keep track of previous subarrays
        if k == 1:
            return nums
        
        current_streak, prev = 1, None
        n = len(nums)
        ans = [0] * (n - k + 1)
        # Get first k-window
        for i in range(k):
            if prev is not None:
                if nums[i] - prev != 1:
                    current_streak = 1
                else:
                    current_streak += 1
            
            prev = nums[i]
                
        ans[0] = prev if current_streak == k else -1
        
        # Iterate through next k-windows
        for i in range(k, n):
            if nums[i] - prev == 1:
                current_streak += 1
                if current_streak >= k:
                    ans[i - k + 1] = nums[i]
                else:
                    ans[i - k + 1] = -1
            else:
                current_streak = 1
                ans[i - k + 1] = -1
            
            prev = nums[i]
                
        return ans
```

- **Time complexity:** $O(n)$
- **Space complexity:** $O(n)$


