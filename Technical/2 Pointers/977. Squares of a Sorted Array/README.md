## 🔗 Problem: [LeetCode #977 - Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/description/)
<br/> <br/> <details> <summary><strong>Difficulty</strong></summary>
> Easy
</details> <details> <summary><strong>🧠 Intuition</strong></summary> <br/>
  
> We need 2 pointers - one on each side of the array. Calculate the square on each side and insert whch is "greater". 

</details> <details> <summary><strong>🛠️ Approach</strong></summary> <br/>

> Initialize 2 pointers - left, right. To keep it simple and to cover all the edge cases start inserting from the end in our result array.
> Calculate the square on both the sides and insert the one which is greater and udpate the pointer accordingly.

</details> <details> <summary><strong>⏱️ Complexity</strong></summary> <br/>
  
| Type | Complexity |
|------|------------|
| Time | O(n)      |
| Space| O(n)      |

We only scan the array once and use output extra array.</details> <details> <summary><strong>💻 Code (Python)</strong></summary> <br/>

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        l, r, k = 0, len(nums) - 1, len(nums) - 1
        res = [0]*len(nums)

        while l <= r:
            x = nums[l]*nums[l]
            y = nums[r]*nums[r]

            if x > y:
                res[k] = x
                l += 1
            else:
                res[k] = y
                r -= 1
            k -= 1

        return res
```
</details>
