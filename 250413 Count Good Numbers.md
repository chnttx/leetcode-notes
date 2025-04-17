https://leetcode.com/problems/count-good-numbers

```python
class Solution:
    def countGoodNumbers(self, n: int) -> int:
        mod = 1000000007
        return pow(5, int((n + 1) // 2), mod) * pow(4, int(n // 2), mod) % mod
```

