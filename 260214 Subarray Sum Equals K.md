https://leetcode.com/problems/subarray-sum-equals-k/description/

first thoughts: since `nums[i]` can be negative, there can theoretically be multiple subarrays ending at index N, so sliding windows would not have any conditions to move forwards/backwards deterministically.

A better approach would be to store the frequencies of the sum up to index i for 0 < i < n, then with each iteration do `target = current_sum - k` -> get `freq[target]`

```python
for num in nums:
	curr += num
	ans += frequencies.get(curr - k)
	frequencies[curr] += 1
```