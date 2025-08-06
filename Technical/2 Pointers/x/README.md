## 🔗 [Problem: LeetCode #2570 – Merge Two 2D Arrays by Summing Values](https://leetcode.com/problems/merge-two-2d-arrays-by-summing-values/description/)
<br/> <br/> <details> <summary><strong>Difficulty</strong></summary> <br/> Easy </details> <details> <summary><strong>🧠 Intuition</strong></summary> <br/>

Since both 2D arrays are sorted by the first element, we can use a two-pointer approach (similar to merge sort) to traverse them efficiently.
This helps us add values where IDs match, and insert directly where they don’t.
</details> <details> <summary><strong>🛠️ Approach</strong></summary> <br/>

We initialize two pointers at the start of each array (nums1, nums2).

    If the IDs are equal, we add the values and move both pointers forward.

    If nums1 has a smaller ID, we add its value as-is and move its pointer.

    If nums2 has a smaller ID, we do the same for it.

Once one of the arrays is exhausted, we add the remaining elements from the other array.

📌 Alternate approach to remember:
If constraints are tight (e.g., max ID ≤ 1000), we can use a fixed-length array for summing (constant space). Set MAX = 1000 and pre-allocate a counting array.
</details> <details> <summary><strong>⏱️ Complexity</strong></summary> <br/>

  | Type | Complexity |
|------|------------|
| Time | O(n + m)       |
| Space| O(1) extra (excluding result list)      |

n = len(nums1), m = len(nums2) We only use two pointers and no extra data structure.</details> <details> <summary><strong>💻 Code (Python)</strong></summary> <br/>

class Solution:
    def mergeArrays(self, nums1: List[List[int]], nums2: List[List[int]]) -> List[List[int]]:
        l, r = 0, 0
        res = []
        
        while l < len(nums1) and r < len(nums2):
            id1, val1 = nums1[l]
            id2, val2 = nums2[r]
            
            if id1 == id2:
                res.append([id1, val1 + val2])
                l += 1
                r += 1
            elif id1 < id2:
                res.append([id1, val1])
                l += 1
            else:
                res.append([id2, val2])
                r += 1
        
        while l < len(nums1):
            res.append(nums1[l])
            l += 1
            
        while r < len(nums2):
            res.append(nums2[r])
            r += 1
        
        return res

📌 Alternate O(1001) Space Version for Remembering:

class Solution:
    def mergeArrays(self, nums1: List[List[int]], nums2: List[List[int]]) -> List[List[int]]:
        MAX = 1000
        count = [0] * (MAX + 1)
        
        for i, v in nums1:
            count[i] += v
        for i, v in nums2:
            count[i] += v
        
        return [[i, count[i]] for i in range(MAX + 1) if count[i] > 0]

</details>
