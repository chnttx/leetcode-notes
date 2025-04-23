https://leetcode.com/classic/problems/count-largest-group/description/

```python
class Solution:
    def digitSum(self, num: int) -> int:
        ans = 0
        while num > 0:
            num, r = divmod(num, 10)
            ans += r
        return ans
    def countLargestGroup(self, n: int) -> int:
        dct = defaultdict(int)
        for i in range(1, n + 1):
            dct[self.digitSum(i)] += 1
        _max = max(dct.values())
        return len([k for k, v in dct.items() if v == _max])
```

- **Time complexity**: $O(nlogn)$.
- **Space complexity**: $O(logn)$.