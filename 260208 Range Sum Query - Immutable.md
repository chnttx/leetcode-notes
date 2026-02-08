https://leetcode.com/problems/range-sum-query-immutable/

first thoughts: because they were asking for sum of the elements between `left` and `right`, we'd need to keep track of the sum of nums up to left and right. Prefix sum comes to mind

Another thing to consider is that since we only init nums once, and nums is immutable, it's better to calculate prefix sum array during init as well

```python
return self.prefixSum[right + 1] - self.prefixSum[left]
```