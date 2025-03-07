https://leetcode.com/classic/problems/closest-prime-numbers-in-range

## Intuition

- Since we have to generate prime numbers up to `right`, prime number generating algorithms make sense in this case. The most common one is sieve of Erathosthenes.
- Possible optimisations could include only starting from `sqrt(left)`.

```python
class Solution:
    def closestPrimes(self, left: int, right: int) -> List[int]:
        prime = [True] * (right + 1)
        prime[1] = False
        p = 2
        ans_left, ans_right, l, r = -1, -1, 0, 0
        diff = float('inf')
        while p * p <= right:
            if prime[p]:
                for i in range(p * p, right + 1, p):
                    prime[i] = False

            p += 1

        for i in range(left, right + 1):
            if prime[i]:
                print(i)
                if not l:
                    l = i
                elif l and not r:
                    r = i
                    diff = r - l
                    ans_left, ans_right = l, r
                else:
                    l = r
                    r = i
                    if r - l < diff:
                        ans_left, ans_right = l, r
                        diff = min(diff, r - l)

        return [ans_left, ans_right]
```

- **Time complexity**: $O(right * log(log(right)))$
- **Space complexity**: $O(right)$
