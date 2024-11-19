https://leetcode.com/problems/defuse-the-bomb/

### Brute-force approach

```python
class Solution:
    def nxt(self, nums: List[int], k: int, n: int) -> List[int]:
        ans = [0] * n
        for i in range(n):
            for j in range(1, k + 1):
                ans[i] += nums[(i + j) % n]
                
        return ans
                
    
    def prev(self, nums: List[int], k: int, n: int) -> List[int]:
        ans = [0] * n
        for i in range(n):
            for j in range(1, -k + 1):
                ans[i] += nums[(i - j) % n]
                
        return ans
    
    def decrypt(self, code: List[int], k: int) -> List[int]:
        
        n = len(code)
        
        if k == 0:
            return [0] * n
        
        elif k > 0:
            return self.nxt(code, k, n)
        
        else:
            return self.prev(code, k, n)
```

- **Time complexity:** $O(k*n)$
- **Space complexity:** $O(n)$

### Optimized approach

- **Basic idea:** sliding window