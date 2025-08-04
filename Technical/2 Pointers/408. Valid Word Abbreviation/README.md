## 🔗 Problem: [LeetCode #408 – Valid Word Abbreviation](https://leetcode.com/problems/valid-word-abbreviation/description/)

<br/>
<br/>
<strong>Difficulty: </strong>Easy
<br/>

---


<details>
<summary><strong>🧠 Intuition</strong></summary>

<br/>
Use two pointers — one for word, one for abbr. Focus on 2 cases: if character in abbr is digit or alphabet. Write your conditions based on that. 

    When abbr[j] is a digit, parse the full number (no leading zero) and skip that many letters in word.

    When it's a letter, it must match exactly the corresponding character in word.

    Abbreviation is valid only if both strings are consumed fully.

</details>

---

<details>
<summary><strong>🛠️ Approach</strong></summary>

<br/>
Initialize i = 0 (for word) and j = 0 (for abbr).
Loop while i < len(word) and j < len(abbr):
  If abbr[j] is a letter, ensure it matches word[i], then increment both pointers.
      If abbr[j] is a digit:

          Reject if it's '0' — leading zeros aren’t allowed.

          Parse the full number (loop while digits), advance j accordingly.

          Increase i by the parsed number to skip characters in word.

      At the end, return True only if i == len(word) and j == len(abbr).
This method runs in O(n + m) time and uses O(1) extra space.

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
    def validWordAbbreviation(self, word: str, abbr: str) -> bool:
        
        def isNumeric(c):
            return ('0' <= c <= '9')
        
        def isAlphabet(c):
            return ('a' <= c <= 'z') or ('A' <= c <= 'Z')
        
        i, j = 0, 0

        while i < len(word) and j < len(abbr):
            if isNumeric(abbr[j]):
                if abbr[j] == "0":
                    return False
                snum = ''
                while j < len(abbr) and isNumeric(abbr[j]):
                    snum += abbr[j]
                    j += 1
                i += int(snum)
            else:
                if i >= len(word) or word[i] != abbr[j]:
                    return False
                i, j = i + 1, j + 1
        return (i == len(word) and j == len(abbr))
```
</details>
