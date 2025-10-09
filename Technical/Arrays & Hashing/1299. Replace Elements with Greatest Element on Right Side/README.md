## 🔗 Problem: [LeetCode #1299 – Replace Elements with Greatest Element on Right Side](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/description/)

<br/> <br/>

<details> <summary><strong>Difficulty</strong></summary> <br/> Easy </details> <details> <summary><strong>🧠 Intuition</strong></summary> <br/>

For each element in the array, we need to replace it with the greatest element among all the elements to its right, and the last element should become -1.

A naive approach would check all elements to the right for each index, leading to an O(n²) solution.

Instead, we can use a right-to-left traversal, maintaining a running maximum (max_right) as we go. This way, each element is replaced in O(1) time, resulting in a clean and optimal O(n) solution.

<br/> </details> <details> <summary><strong>🛠️ Approach</strong></summary> <br/>

We iterate from right to left while keeping track of the maximum value seen so far (max_right).

Steps:
1. Initialize max_right = -1.
2. For each element (starting from the end):<br/>
    • Temporarily store the current element.<br/>
    • Replace it with max_right.<br/>
    • Update max_right to be the maximum of itself and the stored value.<br/>

This ensures that when we move leftward, max_right always contains the greatest value among all elements to the right of the current index.

<br/> </details> <details> <summary><strong>⏱️ Complexity</strong></summary> <br/>
Type	Complexity<br/>
Time	O(n)<br/>
Space	O(1)<br/>

We only traverse the array once and perform constant work per element.

</details> <details> <summary><strong>💻 Code (Python)</strong></summary> <br/>

```python

from typing import List

class Solution:
    def replaceElements(self, arr: List[int]) -> List[int]:
        max_right = -1
        for i in range(len(arr) - 1, -1, -1):
            arr[i], max_right = max_right, max(max_right, arr[i])
        return arr
```
</details>
