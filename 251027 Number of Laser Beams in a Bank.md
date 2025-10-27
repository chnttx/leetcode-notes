https://leetcode.com/problems/number-of-laser-beams-in-a-bank/description

answer is the sum of possible pairs between 2 consecutive devices

```python
class Solution:
	def numberOfBeams(self, bank: List[str]) -> int
		prev, ans = 0, 0
		for dev in bank:
			cnt = dev.count('1')
			if cnt > 0:
				if prev > 0:
					ans += cnt * prev
				prev = cnt
		return ans
```

- **Time complexity**: $O(m * n)$.
- **Space complexity**: $O(1)$.