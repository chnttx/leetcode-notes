https://leetcode.com/problems/check-if-all-1s-are-at-least-length-k-places-away

```python
class Solution:
    def kLengthApart(self, nums: List[int], k: int) -> bool:
        # we just need to keep track of the current distance between the next 1 and the previous 1
        curr_distance = 0
        seen_1 = False
        for n in nums:
            if n == 1:
                if seen_1 and curr_distance < k:
                    return False
                seen_1 = True
                curr_distance = 0
            else:
                curr_distance += 1

        return True
```
- **Time complexity**: $O(n)$.
- **Space complexity**: $O(1)$.
