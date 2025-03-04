https://leetcode.com/classic/problems/partition-array-according-to-given-pivot

```python
class Solution:
    def pivotArray(self, nums: List[int], pivot: int) -> List[int]:
        left, mid, right = [], [], []

        for n in nums:
            if n < pivot:
                left.append(n)
            elif n == pivot:
                mid.append(n)
            else:
                right.append(n)

        return left + mid + right
```

- **Time complexity**: $O(n)$
- **Space complexity**: $O(n)$