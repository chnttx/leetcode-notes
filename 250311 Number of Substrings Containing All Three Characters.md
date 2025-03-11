https://leetcode.com/problems/number-of-substrings-containing-all-three-characters

- similar #sliding-window approach to yesterday's daily

```python
class Solution:
    def numberOfSubstrings(self, s: str) -> int:
        ans, l, r, n = 0, 0, 0, len(s)
        letter_count = defaultdict(int)
        while r < n:
            letter_count[s[r]] += 1
            
            while len(letter_count) == 3:
                ans += n - r
                letter_count[s[l]] -= 1
                if letter_count[s[l]] == 0:
                    letter_count.pop(s[l])
                l += 1

            r += 1

        return ans
```

- **Time complexity**: $O(n)$.
- **Space complexity**: $O(1)$.