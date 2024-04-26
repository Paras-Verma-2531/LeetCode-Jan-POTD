# April-26
## 1289. Minimum Falling Path Sum II
```java
public class Solution {
    public int minFallingPathSum(int[][] grid) {
        int n = grid.length;
        int[][] dp = new int[n][n];
        // Copy the first row as base case
        for (int i = 0; i < n; i++) {
            dp[0][i] = grid[0][i];
        }

        for (int row = 1; row < n; row++) {
            for (int col = 0; col < n; col++) {
                int minPrev = Integer.MAX_VALUE;
                for (int k = 0; k < n; k++) {
                    if (k != col) {
                        minPrev = Math.min(minPrev, dp[row - 1][k]);
                    }
                }
                dp[row][col] = grid[row][col] + minPrev;
            }
        }
        int minSum = Integer.MAX_VALUE;
        for (int i = 0; i < n; i++) {
            minSum = Math.min(minSum, dp[n - 1][i]);
        }
        return minSum;
    }
}
