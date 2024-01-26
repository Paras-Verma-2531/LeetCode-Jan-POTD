# January-26 

## 576. Out of Boundary Paths
```java
class Solution {
    private int maxCount(int m, int n, int maxMove, int sr, int sc, int[] delRow, int[] delCol, int[][][] dp) {
        if (maxMove < 0)
            return 0;
        if (sr < 0 || sr >= m || sc < 0 || sc >= n)
            return 1;
        if (dp[sr][sc][maxMove] != -1)
            return dp[sr][sc][maxMove];

        int count = 0;
        for (int i = 0; i < 4; i++) {
            int nr = sr + delRow[i];
            int nc = sc + delCol[i];
            count += maxCount(m, n, maxMove - 1, nr, nc,
                    delRow, delCol, dp);
            count %= 1000000007;
        }
        dp[sr][sc][maxMove] = count;
        return count;
    }

    public int findPaths(int m, int n, int maxMove, int sr, int sc) {
        int[] delRow = { -1, 0, 1, 0 };
        int[] delCol = { 0, 1, 0, -1 };
        int[][][] dp = new int[m][n][maxMove + 1];
        for (int[][] layer : dp)
            for (int[] row : layer)
                Arrays.fill(row, -1);
        return maxCount(m, n, maxMove,sr,sc,delRow,delCol, dp);
    }

}
