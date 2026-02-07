https://leetcode.com/problems/minimum-size-subarray-sum/description/

first thoughts: subarray -> sliding window. asking for minimum size -> dynamic sliding window

-> what conditions would we want to resize the window? when the sum in subarray starts going above 'target'

```python
while current_sum >= target:
	ans = min(ans, right - left + 1)
	current_sum -= nums[left]
	left += 1 
```