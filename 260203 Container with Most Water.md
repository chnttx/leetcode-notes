https://leetcode.com/problems/container-with-most-water/

two endpoints: start and end. So brute force would mean O(n^2) nested loop to check all pairs

optimisation: assuming `height[left] <= height[right]` , if right--, then width definitely decreases, height might also decrease. , if left++, width also definitely decreases, but height might increase. By left++, we're pruning all possible containers with left wall `left`(they can't beat what we already considered)

So we start with the widest container, and shrink width gradually and try to increase the limiting height

```python
if height[left] <= height[right]:
	left += 1
	
else:
	right -= 1
```



