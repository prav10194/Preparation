Link: 

Difficulty: Hard

Type: DP

Algorithm: This requires a bit of intuition initially as the most efficient way would be to solve using DP. The best way to understand the solution would be to start with solving the problem using backtracking. 
Assuming we have coins = [1,3,4,5] and we need to find minimum coins for sum = 7 we can create a tree 

<img width="1434" alt="image" src="https://github.com/user-attachments/assets/5b471dbd-8949-41ca-9f23-df6381de277e" />

Now we can see some computations within the tree, for example in the above image if we have computed how to solve 1 (right-hand side) and how many coins are needed for that we can use this knowledge to solve other nodes which after subtracting will result in 1. 

Using DP (again a bit difficult to come up by own) we can compute for each sum from 0 to amount(=7 in this case) by using knowledge of values that have been computed already.

![image](https://github.com/user-attachments/assets/437c5600-cbd0-4d47-aaa7-737d51bf7683)

[Coin Change PDF](322.pdf)

