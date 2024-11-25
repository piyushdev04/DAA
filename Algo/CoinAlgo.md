Time Complexity: O(n×S)

Algorithm
Input:

Array coins[] of coin denominations and amount S.
Steps:

Initialize dp[] array with Integer.MAX_VALUE (large value) and set dp[0] = 0.

For each coin c in coins[]:
   For each amount j from c to S:
If dp[j−c] ≠ ∞, update:
       dp[j]=min(dp[j],1+dp[j−c])
Return dp[S] if it is not Integer.MAX_VALUE, otherwise return -1.

Output:

Minimum coins required or -1 if the amount cannot be made.