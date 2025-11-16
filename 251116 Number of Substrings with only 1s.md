https://leetcode.com/problems/number-of-substrings-with-only-1s

### Intuition
- you can simplify this down to: `how many substrings are there in a string of size n?` after extracting the number of 1s-only clusters and their lengths. With this, a 2-pass solutions is obvious.
- a slight optimisation can be made which skips the 2nd pass altogether. Counting the sum from 1 up to `n` is given by this formula: $n * (n + 1) / 2$, but if we already keep track of the current number of consecutive 1s, then we just need to add `current_count + 1` to the final answer

```python
class Solution: 
    def numSub(self, s: str) -> int:
        modulo = 1e9 + 7
        ans = 0
        # we need to keep track of how many consecutive 1's before the current string
        prev_consecutive_1 = 0
        for d in s:
            if d == '0':
                prev_consecutive_1 = 0
            else:
                prev_consecutive_1 += 1
                ans += prev_consecutive_1

        return int(ans % modulo)
```

- **Time complexity**: $O(n)$.
- **Space complexity**: $O(1)$.
