https://leetcode.com/classic/problems/find-numbers-with-even-number-of-digits/description/

```python
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        powers10 = {
            1: 1,
            10: 2,
            100: 3,
            1000: 4,
            10000: 5,
            100000: 6
        }
        countDigit = lambda x: int(math.ceil(math.log10(x)))
        ans = 0
        for n in nums:
            ans = ans + 1 if powers10.get(n, countDigit(n)) % 2 == 0 else ans
        return ans
```

- **Time complexity**: $O(nlogn)$.
- **Space complexity**: $O(1)$.