https://leetcode.com/problems/valid-sudoku/
## Intuition

- Doing this instead of using 3 separate hash tables for row, col and square is simpler while still maintaining uniqueness of every key

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        seen = set()
        for row in range(9):
            for col in range(9):
                if board[row][col] != ".":
                    rkey = str(row) + "({})".format(board[row][col])
                    ckey = "({})".format(board[row][col]) + str(col)
                    skey = str(row // 3) + "({})".format(board[row][col]) + str(col // 3)

                    if rkey in seen or ckey in seen or skey in seen:
                        return False
                    seen.add(rkey)
                    seen.add(ckey)
                    seen.add(skey)

        return True
```

- **Time complexity**: $O(1)$, constraint fixed
- **Space complexity**: $O(1)$, constraint fixed
