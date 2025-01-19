Link: https://leetcode.com/problems/n-queens/description/

Level: Hard

Type: Backtracking

Algorithm: Create 3 sets for cols, posDig, negDig (rows is not needed as a set as we will be backtracking on rows). We need to find all possible combinations to set our Queen pieces on the n x n board.We will be backtracking on row number as there can be only one Queen in one row. Create three sets for column, positive diagonal (r+c will be same) and negative diagonal (r-c will be same).  

<img width="374" alt="image" src="https://github.com/user-attachments/assets/785cec5d-a56e-4105-8447-de6f8141857c" />

For each row, don't add into the set if either of c, r+c or r-c is not unique. Add if unique, and backtrack to next row. In case of any of the sets already filled for that value, remove the last added value and repeat the process.

[N Queens PDF](79.pdf)
