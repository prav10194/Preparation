## 🔗 Problem: [LeetCode #392 – Is Subsequence](https://leetcode.com/problems/is-subsequence/description/)
<br/> <br/> 
<details> 
<summary><strong>Difficulty</strong></summary> 
<br/> 
Easy 
</details> 

<details> 
<summary><strong>🧠 Intuition</strong></summary> 
<br/>

> We need to check whether string <code>s</code> appears in <code>t</code> **in order** (not necessarily contiguously).  
> A simple **two-pointer** scan works perfectly: walk through <code>t</code>, advancing the pointer in <code>s</code> whenever we match the next needed character.

<br/>
</details> 

<details> 
<summary><strong>🛠️ Approach</strong></summary> 
<br/>

> 1️⃣ If <code>s</code> is empty, return <code>True</code>.  
> 2️⃣ Keep a pointer <code>i</code> for <code>s</code>. Iterate characters of <code>t</code>:  
> &nbsp;&nbsp;&nbsp;&nbsp;• When <code>t[j] == s[i]</code>, increment <code>i</code>.  
> &nbsp;&nbsp;&nbsp;&nbsp;• If <code>i</code> reaches <code>len(s)</code>, we matched all chars in order → return <code>True</code>.  
> 3️⃣ After the loop, return whether we consumed all of <code>s</code>.  
>
> 🔁 **One-liner alternative:** Use an iterator of <code>t</code> and check <code>all(c in it for c in s)</code>.

<br/>
</details> 

<details> 
<summary><strong>⏱️ Complexity</strong></summary> 
<br/>

| Type | Complexity |
|------|-------------|
| Time | O(|t|) |
| Space | O(1) |

</details> 

<details> 
<summary><strong>💻 Code (Python)</strong></summary> 
<br/>

```python
from typing import List

class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        """Return True if s is a subsequence of t using a two-pointer scan.
        Time: O(len(t)), Space: O(1)
        """
        # Fast path: empty s is always a subsequence
        if not s:
            return True

        i = 0  # pointer into s
        for ch in t:
            if ch == s[i]:
                i += 1
                if i == len(s):  # found all chars in order
                    return True
        return False


# Optional: succinct equivalent using iter()
def is_subsequence_iter(s: str, t: str) -> bool:
    it = iter(t)
    return all(c in it for c in s)
```

</details>

<details>
<summary><strong>📈 Follow-up (multiple queries)</strong></summary>
<br/>

> If you must check many different <code>s</code> strings against the same (long) <code>t</code>, preprocess <code>t</code> by storing the sorted list of indices for each character (e.g., <code>pos['a'] = [indices...]</code>).  
> Then, for each <code>s</code>, walk its chars and binary-search the next index greater than the current pointer. This makes each query run in <code>O(|s| log Σ)</code> where Σ is the alphabet size.

</details>
