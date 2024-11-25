Time Complexity:

O(n×k) where k are the inputs. This is because we need to fill a table of size (n+1)×(k+1)

Algorithm for Binomial Coefficient:
Input:

Two integers, n and k.

Steps:

- Initialize a 2D array dp[][] of size (n+1)×(k+1).

- Set base values: dp[i][0] = 1 and dp[i][i] = 1.

- Use the recurrence relation to fill the table:

         dp[i][j]=dp[i−1][j−1]+dp[i−1][j]

- Return the value at dp[n][k].

Output:

The value of C(n,k), which is stored in dp[n][k].