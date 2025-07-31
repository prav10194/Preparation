## 🔗 Problem: [LeetCode #125 – Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)

<br/>
<br/>
<details>
<summary><strong>Difficulty</strong></summary>

<br/>
Easy

</details>

---


<details>
<summary><strong>🧠 Intuition</strong></summary>

<br/>
Since we need to validate the palindrome, 2 Pointers make sense. 

</details>

---

<details>
<summary><strong>🛠️ Approach</strong></summary>

<br/>
We would effectively want to run one from left and another from right and return False if any of the combination doesn't match. 
Also we need to skip on Alphanumeric and convert everythign to lower case to make it easy.

</details>

---

<details>
<summary><strong>⏱️ Complexity</strong></summary>
<br/>

| Type | Complexity |
|------|------------|
| Time | O(?)       |
| Space| O(?)       |

<!--
Explain why this is the time/space complexity.
Mention edge cases or tradeoffs if relevant.
-->

</details>

---

<details>
<summary><strong>💻 Code (Python)</strong></summary>
<br/>

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        
        def isAlphanumeric(char):
            return ('A' <= char <= 'Z') or ('a' <= char <= 'z') or ('0' <= char <= '9')

        def convertToLower(char):
            if 'A' <= char <= 'Z':
                return chr(ord(char) + 32)
            else:
                return char
    
        l, r = 0, len(s) - 1
        while l <= r:
            if isAlphanumeric(s[l]) and isAlphanumeric(s[r]):
                if convertToLower(s[l]) != convertToLower(s[r]): return False
                l += 1
                r -= 1
            else:
                if not isAlphanumeric(s[l]): 
                    l += 1
                if not isAlphanumeric(s[r]): 
                    r-= 1
        return True
```
</details>
