https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/

### `Counter` approach

- **Notes**
	- Keep track of number of distinct elements in window instead of calling `len(current_window)` every time. This brings down time complexity from $O(k*n)$ to $O(n)$

```python
class Solution:
    def maximumSubarraySum(self, nums: List[int], k: int) -> int:
        
        l, r, n = 0, k, len(nums) 
        current_subarray_sum = sum(nums[l:r])
        current_window = Counter(nums[l:r])
        current_window_element_count = len(current_window)
        ans = current_subarray_sum if len(current_window) == k else 0
        
        while r < n:
            current_subarray_sum += nums[r] - nums[l]
            current_window_element_count = current_window_element_count + 1 if nums[r] not in current_window else current_window_element_count
           
            current_window[nums[r]] += 1
            current_window[nums[l]] -= 1
            if current_window[nums[l]] == 0:
                current_window_element_count -= 1
                del current_window[nums[l]]
            
            if current_window_element_count == k:
                ans = max(ans, current_subarray_sum)
            
            l += 1
            r += 1
        
        return ans
```

- **Time complexity:** $O(n)$
- **Space complexity:** $O(k)$

### `set` approach

- **Notes**
	- Need to handle element removal when there are duplicate elements
