https://leetcode.com/problems/count-and-say/

```python
class Solution:
    def countAndSay(self, n: int) -> str:
        if n == 1:
            return "1"
        
        prev = self.countAndSay(n - 1)
        run = []
        for c in prev:
            if not run or run[-1][1] != c:
                run.append([1, c])
            else:
                run[-1][0] += 1
            
        return "".join([f"{count}{ch}" for count, ch in run])
```

- **Time complexity**: $O(n ^2)$.
- **Space complexity**: $O(n^2)$, because each call of `countAndSay` takes $O(n)$, and there are `n` calls. 