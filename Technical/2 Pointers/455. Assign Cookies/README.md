## 🔗 Problem: [LeetCode #455 - Assign Cookies](https://leetcode.com/problems/assign-cookies/description/)
<br/> <br/> <details> <summary><strong>Difficulty</strong></summary> <br/> 
> Easy
</details> <details> <summary><strong>🧠 Intuition</strong></summary> <br/>
  
> Logically I would have thought this would be a DP problem but with O(mlogm + nlogn) we can find an easier way using 2 pointers. 
<br/>
</details> <details> <summary><strong>🛠️ Approach</strong></summary> <br/>

> Step 1: Sort both the arrays - O(nlogn) operation.
> <br/><br/>
> Step 2: Create 2 pointers, L and R that will traverse each of the arrays - greed and size.
> <br/><br/>
> Step 3: While traversing, compare if the g[L] <= s[R], <u>if yes</u> then increment both the pointers.
> <br/> <u>If not</u>, find the value in array s that will satisfy the condition (as the arrays are sorted).
> <br/><br/>
> Step 4: Return pointer L.

</details> <details> <summary><strong>⏱️ Complexity</strong></summary> <br/>
  
| Type | Complexity |
|------|------------|
| Time | O(nlogn + mlogm)      |
| Space| O(1)      |

</details> <details> <summary><strong>💻 Code (Python)</strong></summary> <br/>

```python
class Solution:
    def findContentChildren(self, g: List[int], s: List[int]) -> int:
        g.sort()
        s.sort()

        l, r = 0, 0
        
        while l < len(g):
            while r < len(s) and g[l] > s[r]:
                r += 1
            if r == len(s):
                break
            l += 1
            r += 1
        return l
```
</details>
