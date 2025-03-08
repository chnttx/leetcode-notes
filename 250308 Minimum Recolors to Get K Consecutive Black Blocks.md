https://leetcode.com/problems/minimum-recolors-to-get-k-consecutive-black-blocks
### Intuition

- `consecutive` hints that we have to use #sliding-window approach. We maintain a window of fixed size `k`, as our window moves through array, maintain minimum of white blocks in any window. The final result will be minimum number of white blocks of any window.

```python
class Solution:
    def minimumRecolors(self, blocks: str, k: int) -> int:
        w, n, l, ans = 0, len(blocks), 0, k
        for i in range(k):
            if blocks[i] == "W":
                w += 1
        
        for i in range(k, n):
            if blocks[i] == "W":
                w += 1
                ans = min(ans, w)
            if blocks[l] == 'W':
                w -= 1
            
            l += 1
        
        return ans
```

- **Time complexity**: $O(n)$
- **Space complexity**: $O(1)$
