https://leetcode.com/classic/problems/check-if-number-is-a-sum-of-powers-of-three/description/

## Intuition

- We can rephrase this problem to "Can we write a decimal number in base 3, but without using 2", since `distinct powers of 3`.
- i.e. 12 can be written as $3^1 + 3^2$, so in base 3 it would be `110`, but 18 cannot because it's $3^2 + 3^2$, or `200` in base 3.
- To convert a decimal number to base-n, we can use the following algorithm:

```python
def convertToBaseK(n, k):
	ans = []
	while n > 0:
		n, remainder = divmod(n, k)
		ans.append(remainder)
	return "".join(reverse(ans))	 
```

```python
class Solution:
    def checkPowersOfThree(self, n: int) -> bool:
        current = 0

        while n > 0:
            n, r = divmod(n, 3)
            if r == 2:
                return False

        return True
```

- **Time complexity**: $O(logn)$
- **Space complexity**: $O(1)$