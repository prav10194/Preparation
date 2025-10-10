# 🔗 Problem: [LeetCode – Append Characters to String to Make Subsequence](https://leetcode.com/problems/append-characters-to-string-to-make-subsequence/description/)

<details>
<summary><strong>Difficulty</strong></summary>
<br/>
Easy
</details>

<details>
<summary><strong>🧠 Intuition</strong></summary>
<br/>
We want the smallest number of characters to append to the end of <code>s</code> so that <code>t</code> becomes a subsequence of the new string.  
If we greedily match as many characters of <code>t</code> as possible inside <code>s</code> (in order), whatever remains unmatched in <code>t</code> must be appended.  
So the answer is simply: <code>|t| - (# of characters of t we could match in s)</code>.
</details>

<details>
<summary><strong>🛠️ Approach</strong></summary>
<br/>

**Two Pointers**

- Let `i` scan `s` and `j` scan `t`.  
- Move `i` from left to right.  
- Whenever `s[i] == t[j]`, advance `j` (we “consume” a needed character of `t`).  
- At the end, we matched `j` characters from `t`. The rest `|t| - j` must be appended.

This is optimal because subsequence matching is order-preserving; there’s no benefit to skipping a match you could take greedily.
</details>

<details>
<summary><strong>🧪 Examples</strong></summary>
<br/>

**Example 1**  
- `s = "coaching"`, `t = "coding"`  
- Greedy match in order: **c**o**a**ch**i**ng vs **c**od**i**ng → matched `"coin"` (length 4).  
- Need `|t| - matched = 6 - 4 = 2` → append `"dg"`.

**Example 2**  
- `s = "abc"`, `t = "abccba"`  
- We can match `"abc"` inside `s` (length 3).  
- Need `6 - 3 = 3` more → append `"cba"`.

**Example 3**  
- `s = ""`, `t = "xyz"` → matched `0`, need `3`.
</details>

<details>
<summary><strong>🧩 Edge Cases</strong></summary>
<br/>

- `t` already a subsequence of `s` → answer `0`.  
- Empty `t` → answer `0`.  
- Empty `s` → answer `|t|`.  
- Repeated characters in `t` (ensure the greedy pointer only advances on equality).
</details>

<details>
<summary><strong>⏱️ Complexity</strong></summary>
<br/>

- **Time:** `O(|s| + |t|)` (each pointer moves at most once across its string)  
- **Space:** `O(1)`
</details>

---

## ✅ Reference Implementations

### Python
```python
def append_characters(s: str, t: str) -> int:
    i = j = 0
    n, m = len(s), len(t)
    while i < n and j < m:
        if s[i] == t[j]:
            j += 1
        i += 1
    return m - j
```
