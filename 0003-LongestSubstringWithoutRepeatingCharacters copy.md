# 3) Longest Substring Without Repeating Characters

## First submission (351 ms)

A recursive method that processes each character of the string. For each character, the loop continues until a repeat occurs, and then the code moves on to the next character. In simpler terms, this results in many unnecessary loops being executed.

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        sub = ""
        n = len(s)
        if n == 0:
            m = 0
        else:
            m = 1
        rg = range(n)
        for i in rg:
            x = s[i]
            if not x in sub:
                sub += x
            else:
                m = max(self.lengthOfLongestSubstring(s[1:]), len(sub), m)
                break
        return max(m, len(sub))
```

## Second submission (11 ms)

In this solution, I created a visited `set` that collects characters until a repeat is encountered. As each character is processed, the answer is updated by taking the maximum between the current longest substring and the new one formed by counting the non-repeated characters. When a repeat occurs, all characters up to the first occurrence of the repeated character are removed from the visited set, and the number of characters deleted is tracked by a variable `j` (which indicates that we are now counting from that index). While there are still some extra overheads, I didn't focus on optimizing that part further.

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:

        m = 0
        visited = set()
        j = 0
        rg = range(len(s))

        for i in rg:
            while s[i] in visited:
                visited.remove(s[j])
                j += 1
            m = max(m, i - j + 1)
            visited.add(s[i])
        return m
```
