## 🔗 Problem: [LeetCode #3 – Longest Substring Without Repeating Characters](https://leetcode.com/problems/move-zeroes/description/)

<br/> <br/>

<details> <summary><strong>Difficulty</strong></summary> <br/> Easy </details> <details> <summary><strong>🧠 Intuition</strong></summary> <br/>

We need to find the longest substring that contains all unique characters — i.e., no character repeats.

A two-pointer (sliding window) approach works best. We maintain a window that always contains unique characters.

As we expand the right pointer, we check for duplicates:<br/>
– If a duplicate is found, we move the left pointer just past the previous occurrence of that character.<br/>
– This ensures that the window always remains valid (all unique).

<br/> </details> <details> <summary><strong>🛠️ Approach</strong></summary> <br/>

1. We would be using 2 pointers, left = to keep track of the last seen charcter (and updated accordingly). <br/>
   right = iterate the input string. 
2. Use a dictionary seen to store the last index where each character appeared.
3. For each character s[right]:<br/>
    • If it was seen before and is inside the current window, move left to seen[ch] + 1.<br/>
    • Update seen[ch] = right.<br/>
4. Compute the current window size as right - left + 1 and update the maximum.
<br/>

This ensures each character is processed at most twice — once when entering the window and once when being removed.

<br/> </details> <details> <summary><strong>⏱️ Complexity</strong></summary> <br/>
Time	= O(n) <br/>
Space	O(k), where k is the number of unique characters
<br/>
We scan each character once, maintaining a sliding window and a hash map for constant-time lookups.

</details> <details> <summary><strong>💻 Code (Python)</strong></summary> <br/>
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        seen = {}       # character -> last seen index
        left = 0
        max_len = 0

        for right, c in enumerate(s):
            if c in seen and seen[ch] >= left:
                left = seen[c] + 1   # move left pointer past the duplicate
            seen[c] = right
            max_len = max(max_len, right - left + 1)

        return max_len
</details>
