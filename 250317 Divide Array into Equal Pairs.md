### Intuition

- Check if frequency of each element is divisible by 2

```python
class Solution:
def divideArray(self, nums: List[int]) -> bool:
	cnt = Counter(nums)
	return all([val % 2 == 0 for val in cnt.values()])
```

- **Time complexity**: $O(n)$.
- **Space complexity**: $O(n)$.