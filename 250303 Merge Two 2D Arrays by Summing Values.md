https://leetcode.com/classic/problems/merge-two-2d-arrays-by-summing-values

- **Intuition**: Because both arrays is sorted ascending, and final answer has to also be sorted ascending, using two pointers - one for each array, is most efficient ($O(m + n)$) compared to sorting final output ($O((m + n)log(m + n))$)

```python
class Solution:
    def mergeArrays(self, nums1: List[List[int]], nums2: List[List[int]]) -> List[List[int]]:
        idx1, idx2 = 0, 0
        n1, n2 = len(nums1), len(nums2)
        ans = defaultdict(int)
        extra = []
        while idx1 < n1 and idx2 < n2:
            if nums1[idx1][0] <= nums2[idx2][0]:
                ans[nums1[idx1][0]] += nums1[idx1][1]
                idx1 += 1
            else:
                ans[nums2[idx2][0]] += nums2[idx2][1]
                idx2 += 1

        if idx1 < n1:
            extra = nums1[idx1:]
        else: # idx2 < n2
            extra = nums2[idx2:]
        
        res = [[k, v] for k, v in ans.items()]
        if extra[0][0] == res[-1][0]:
            res[-1][1] += extra[0][1]
            return res + extra[1:]
        
        return res + extra
```

- **Time complexity**: $O(m + n)$
- **Space complexity**: $O(m + n)$
