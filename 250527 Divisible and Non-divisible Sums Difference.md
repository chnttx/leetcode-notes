https://leetcode.com/problems/divisible-and-non-divisible-sums-difference

```python
class Solution:
    def differenceOfSums(self, n: int, m: int) -> int:
        n1 = n * (n + 1) // 2
        n2 = 0
        for i in range(m, n + 1, m):
            n2 += i
            n1 -= i
        return n1 - n2
```

- **Time complexity**: $O(n - m)$.
- **Space complexity**: $O(1)$.