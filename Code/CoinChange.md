import java.util.Arrays;
import java.util.Scanner;

public class CoinChange {

    public static int minCoins(int[] coins, int amount) {
        
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, Integer.MAX_VALUE);
        dp[0] = 0; 

        for (int coin : coins) {
            for (int j = coin; j <= amount; j++) {
                if (dp[j - coin] != Integer.MAX_VALUE) {
                    dp[j] = Math.min(dp[j], 1 + dp[j - coin]);
                }
            }
        }

        return dp[amount] == Integer.MAX_VALUE ? -1 : dp[amount];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
       
        System.out.print("Enter the number of coin types: ");
        int n = scanner.nextInt();

        int[] coins = new int[n];
        System.out.println("Enter the coin denominations:");
        for (int i = 0; i < n; i++) {
            coins[i] = scanner.nextInt();
        }
    
        System.out.print("Enter the amount: ");
        int amount = scanner.nextInt();
       
        int result = minCoins(coins, amount);

        if (result != -1) {
            System.out.println("Minimum number of coins required: " + result);
        } else {
            System.out.println("It is not possible to make the given amount with the available coins.");
        }

        scanner.close();
    }
}