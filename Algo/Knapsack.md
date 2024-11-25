Time Complexity: O(n×W)

Algorithm
Input:

Number of items 

n, arrays weights[] and values[], and knapsack capacity W.
Steps:

Initialize a 2D table dp[n+1][W+1] with zeros.
Iterate through items i=1 to n:
Iterate through capacities w=1 to W:
If weights[i−1]≤w:
dp[i][w]=max(dp[i−1][w],values[i−1]+dp[i−1][w−weights[i−1]])
Otherwise:
dp[i][w]=dp[i−1][w]
Return dp[n][W] as the result.
Output:

Maximum value for the knapsack capacity.