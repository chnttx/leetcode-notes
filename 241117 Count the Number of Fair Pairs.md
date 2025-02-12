https://leetcode.com/problems/count-the-number-of-fair-pairs/

Given a **0-indexed** integer array `nums` of size `n` and two integers `lower` and `upper`, return _the number of fair pairs_.

A pair `(i, j)` is **fair** if:

- `0 <= i < j < n`, and
- `lower <= nums[i] + nums[j] <= upper`

**Example 1:**

**Input:** nums = [0,1,7,4,4,5], lower = 3, upper = 6
**Output:** 6
**Explanation:** There are 6 fair pairs: (0,3), (0,4), (0,5), (1,3), (1,4), and (1,5).

**Example 2:**

**Input:** nums = [1,7,9,2,5], lower = 11, upper = 11
**Output:** 1
**Explanation:** There is a single fair pair: (2,3).

#### Notes

- sorting + binary search
### Naive approach

- **Main idea:** loop through every pair
- **Time complexity:** $O(n^2)$
- **Space complexity:** $O(1)$

### More efficient approach

- **Main idea:** #sorting  #binary-search
- **Algorithm: (THIS DOESN'T WORK WHEN `lower == upper`)**
	1. Sort array
	2. For each number in array:
		1. binary search to find leftmost idx s.t. number + `nums[idx]` >= lower and rightmost idx s.t. number + `num[idx]` <= upper
		2. number of pairs is `right idx - left idx + 1`

- **Time complexity:** $O(nlogn)$
- **Space complexity**: $O(n)$ (`.sort()` in python uses merge sort and insertion sort)

- **ALGORITHM THAT ACTUALLY WORKS:**
- 



