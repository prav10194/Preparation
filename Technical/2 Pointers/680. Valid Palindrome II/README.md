## 🔗 Problem: [LeetCode #680 – Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/description/)

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
Since we are allowed one removal - break the problem where left doesn't match right and then run palindrome on 2 substrings (each having one element is removed from either side).

</details>

---

<details>
<summary><strong>🛠️ Approach</strong></summary>

<br/>


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
    def validPalindrome(self, s: str) -> bool:

        def isPalindrome(subs):
            subl, subr = 0, len(subs) - 1
            
            while subl < subr:
                if subs[subl] != subs[subr]:
                    return False
                subl += 1
                subr -= 1
            return True

        
        l, r = 0, len(s) - 1

        while l < r:
            if s[l] != s[r]:
                return isPalindrome(s[l+1:r+1]) or isPalindrome(s[l:r])
            l += 1
            r -= 1
        return True

```
</details>
