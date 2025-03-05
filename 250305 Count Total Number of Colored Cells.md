https://leetcode.com/classic/problems/count-total-number-of-colored-cells
## Intuition

![[Pasted image 20250305114959.png]]

- We can see from the picture that at stage n, there are n layers, each with n squares, and n - 1 layers each with n - 1 squares. Therefore the general formula is $n^2 + (n - 1)^2$

```python
class Solution:
    def coloredCells(self, n: int) -> int:
        return n ** 2 + (n - 1) ** 2
```

- **Time complexity**: $O(1)$
- **Space complexity**: $O(1)$