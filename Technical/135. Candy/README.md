Link: https://leetcode.com/problems/candy/description/

Difficulty: Hard

Type: 2 passes

Algorithm: Algorithm is easy to understand, you start with 2 passes - first with all the left neighbors (left -> right) and updating the candy array. Next we continue with looking at all the right neighbors (right -> left). Update the values if ratings of the neighbors vary. 

Initially we start with giving everyone with 1 candy. In the example below, we are executing our first pass and for index = 3 we will update the value as left neighbor is less than current value. 

<img width="468" alt="image" src="https://github.com/user-attachments/assets/b9188d67-2125-4961-81a3-8b2c77278cf8" />

[Candy Problem PDF](135.pdf)

