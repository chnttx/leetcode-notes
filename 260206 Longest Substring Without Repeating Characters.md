https://leetcode.com/problems/longest-substring-without-repeating-characters/description/

first thoughts: substring -> sliding window. They asked 'longest' so would have to be dynamic sliding window

the question then becomes as we keep moving right, when do we start moving left?

the window becomes invalid as soon as `s[right` is already in the window, so instead of checking that all letters are unique, we just need to check that `s[right]` is unique

```python
while window[s[right]] > 1:
	window[s[left]] -= 1
	left += 1
```