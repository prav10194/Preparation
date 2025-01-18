Link: https://leetcode.com/problems/trapping-rain-water/description/

Difficulty: Hard

Category: 

Algorithm: Based on the understanding, for each index i - we need to run the logic of checking min(maxLeft, maxRight) and subtracting the value at current index. 

So in image below, water that can be stored at index 6 would be: min(maxLeft=2, maxRight=3) - 0 = 2.

<img width="584" alt="image" src="https://github.com/user-attachments/assets/a9c74d06-ea72-40ff-840f-df0819dd827d" />

Solution 1: Maintaining memory for storing computed values for maxLeft, maxRight and storing min(maxLeft, maxRight). Space complexity: O(n)

<img width="1004" alt="image" src="https://github.com/user-attachments/assets/6f81b826-7f38-416a-8ff5-6706d4e80b9c" />

Solution 2: Maintaining 4 pointers, L and R and LMAX and RMAX. Logic for updating the pointers - if LMAX < RMAX, move L pointer to left and calculate totalWater (doesn't matter if we don't know correct RMAX because LMAX value will be considered for minimum). 

[Trapping Rain Water Problem PDF](42.pdf)

