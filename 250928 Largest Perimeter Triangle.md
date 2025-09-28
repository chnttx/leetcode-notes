https://leetcode.com/problems/largest-perimeter-triangle/description

### Intuition

- To form a triangle, for any 3 lengths `a, b, c`, `a + b > c`
- Because this problem asks for largest perimeter length, we can apply sorting and just return the first triangle we find. It is guaranteed that it would be the largest triangle we can find

### Code

```python
class Solution:
	def largestPerimeter(self, nums: List[int]) -> int:
		# a + b > c for any 3 a, b, c
		nums.sort(reverse=True)
		# the first valid triangle we get would always have largest perimeter
		for i in range(len(nums) - 2):
			a, b, c = nums[i], nums[i + 1], nums[i + 2]
			if b + c > a:
				return b + c + a
		
		return 0
```

- **Time complexity**: $O(nlogn)$
- **Space complexity**: $O(1)$