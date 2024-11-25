import java.util.Scanner;

public class BinomialCoefficient {

    
    public static int binomialCoefficient(int n, int k) {
        
        int[][] dp = new int[n + 1][k + 1];

        
        for (int i = 0; i <= n; i++) {
            dp[i][0] = 1;
        }
        for (int i = 0; i <= k; i++) {
            dp[i][i] = 1;
        }

        
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= Math.min(i, k); j++) {
                dp[i][j] = dp[i - 1][j - 1] + dp[i - 1][j];
            }
        }

        
        return dp[n][k];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        
        System.out.print("Enter n: ");
        int n = scanner.nextInt();
        System.out.print("Enter k: ");
        int k = scanner.nextInt();

        
        int result = binomialCoefficient(n, k);

        
        System.out.println("Binomial Coefficient C(" + n + ", " + k + ") is: " + result);

        scanner.close();
    }
}