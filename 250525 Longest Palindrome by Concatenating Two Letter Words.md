https://leetcode.com/classic/problems/longest-palindrome-by-concatenating-two-letter-words/description/

```python
class Solution:
    def longestPalindrome(self, words: List[str]) -> int:
        odd, even = Counter(), Counter()
        for w in words:
            if w[0] == w[1]:
                even[w] += 1
            else:
                odd[w] += 1

        ans = 0
        for w in odd:
            if w[::-1] in odd:
                ans += 2 * min(odd[w], odd[w[::-1]])
                
        first = True
        for w in even:
            if even[w] % 2 == 0:
                ans += 2 * even[w]
            else:
                if first:
                    ans += 2 * even[w]
                    first = False
                else:
                    ans += 2 * (even[w] - 1)
        
        return ans
```

- **Time complexity**: $O(n)$.
- **Space complexity**: $O(n).