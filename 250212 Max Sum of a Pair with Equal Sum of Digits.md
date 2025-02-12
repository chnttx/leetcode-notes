https://leetcode.com/problems/max-sum-of-a-pair-with-equal-sum-of-digits/

#hash-tables #math

## Approach

- Group `nums` by digit sum, aggregate each group's max sum

```python
class Solution:
    def getDigitSum(self, num: int) -> int:
        ans = 0
        while num > 0:
            ans += num % 10
            num //= 10
        return ans

    def maximumSum(self, nums: List[int]) -> int:
        nums.sort()
        ans = -1
        groupByDigitSum = defaultdict(list)
        for num in nums:
            curr = groupByDigitSum[Solution.getDigitSum(self, num)]
            curr.append(num)
            if len(curr) > 1:
                ans = max(ans, curr[-1] + curr[-2])

        return ans
```

- **Time complexity**: $O(nlogn)$
- **Space complexity**: $O(n)$