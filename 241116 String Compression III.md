https://leetcode.com/problems/string-compression-iii

### Two-pass #stack approach

- **Main idea:** Group each consecutive letter group into `character: frequency` groups, then flatten each group into `{count}{character}` 

```python
class Solution:
    def compressedString(self, word: str) -> str:
        
        # Two-pass solution
        # Pass 1: Build letter groups
        st, prev = [], ""
        for i, c in enumerate(word):
            if c != prev:
                st.append([c, 1])
            else:
                st[-1][1] += 1
            prev = c
        
        comp = ""
        # Pass 2: Compress each letter group
        for ch, cnt in st:
            qt, r = divmod(cnt, 9)
            comp += qt * ('9'+ ch)
            if r:
                comp += str(r) + ch
            
        return comp
```

- **Time complexity:** $O(n)$
- **Space complexity:** $O(n)$

### One-pass approach

- **Main idea:** Keep track of current letter group, if current letter is different from previous letter, reset count to 1, change prev to current letter

```python
class Solution:
    def compressedString(self, word: str) -> str:
        
        # One-pass solution
        prev, count = "", 0
        comp = ""
        for c in word:
            if c != prev:
                qt, r = divmod(count, 9)
                comp += qt * ('9' + prev)
                if r:
                    comp += str(r) + prev
                
                count = 1
            else:
                count += 1
                
            prev = c
        
        # Edge case when final letter is the same as previous group
        
        qt, r = divmod(count, 9)
        comp += qt * ('9' + prev)
        if r:
             comp += str(r) + prev
                
        return comp
```

- **Time complexity:** $O(n)$
- **Space complexity:** $O(n)$