## 🔗 Problem: [LeetCode #283 – Move Zeros](https://leetcode.com/problems/move-zeroes/description/)
<br/> <br/> <details> <summary><strong>Difficulty</strong></summary> <br/> Easy </details> <details> <summary><strong>🧠 Intuition</strong></summary> <br/>
  
> We need to move all 0s to the end of the array, while keeping the order of non-zero elements the same.
  A two-pointer approach makes perfect sense here: one pointer to find the non-zero elements and the other to track where they should go.

<br/>
</details> <details> <summary><strong>🛠️ Approach</strong></summary> <br/>

> We use a pointer last_non_zero to mark the position where the next non-zero element should be placed.

    Iterate through the array:

        If the current number is not zero, we swap it with the value at last_non_zero.

        Then increment last_non_zero.

> This ensures:

    All non-zero elements are moved forward in their original order.

    All 0s are pushed to the back.

</details> <details> <summary><strong>⏱️ Complexity</strong></summary> <br/>
  
| Type | Complexity |
|------|------------|
| Time | O(n)      |
| Space| O(1)      |

We only scan the array once and use no extra data structures.</details> <details> <summary><strong>💻 Code (Python)</strong></summary> <br/>

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        last_non_zero = 0

        for i in range(len(nums)):
            if nums[i] != 0:
                nums[last_non_zero], nums[i] = nums[i], nums[last_non_zero]
                last_non_zero += 1
```
</details>
