https://leetcode.com/problems/count-of-substrings-containing-every-vowel-and-k-consonants-ii

## Intuition

- We can use a #sliding-window -based approach for this problem, since it's asking for substrings. Though with that we'd have to figure out when to shift `left` to the right.
- This problem can be relaxed to "count of substrings containing every vowel and **at least** k consonants". Finding this is a lot easier, since once you reach the first `right` so that the current #sliding-window matches both criteria, every `right + i` will also match both criteria. We find count of substrings that have at least `k` consonants and count of substrings that have at least `k + 1` consonants, and the final answer will be different of that.

```python
class Solution:
    def countOfSubstrings(self, word: str, k: int) -> int:
        def atLeastK(k):
            vowels = defaultdict(int)
            cons = 0
            l, r, n, ans = 0, 0, len(word), 0
            while r < n:
                if word[r] in "aeiou":
                    vowels[word[r]] += 1
                else:
                    cons += 1

                while cons >= k and len(vowels) == 5:
                    ans += n - r
                    if word[l] in "aeoiu":
                        vowels[word[l]] -= 1
                        if vowels[word[l]] == 0:
                            vowels.pop(word[l])
                    else:
                        cons -= 1
                    l += 1

                r += 1

            return ans

        return atLeastK(k) - atLeastK(k + 1)
```

- **Time complexity**: $O(n)$.
- **Space complexity**: $O(1)$.