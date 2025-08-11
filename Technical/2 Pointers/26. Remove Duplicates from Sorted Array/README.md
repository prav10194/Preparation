## 🔗 Problem: [LeetCode #26 - Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

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
We would need 2 pointers, one to keep track of the position we would need to write the unique value. The other will pass through each array one-by-one.

</details>

---

<details>
<summary><strong>🛠️ Approach</strong></summary>

<br/>
Create a pointer w (write) that will keep track of where to write the unique value. 
Start with w = 1 and run a loop that will compare consecutive values in an array and if they are not same, write the value of current value to nums[w].

</details>

---

<details>
<summary><strong>⏱️ Complexity</strong></summary>
<br/>

| Type | Complexity |
|------|------------|
| Time | O(n)       |
| Space| O(1)       |

Since this is in-place substitution, time complexity will be O(n).

</details>

---

<details>
<summary><strong>💻 Code (Python)</strong></summary>
<br/>

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        w = 1
                
        for l in range(1, len(nums)):
            if nums[l - 1] != nums[l]:
                nums[w] = nums[l]
                w += 1
        return w
```
</details>
