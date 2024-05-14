# May-14
## 1219. Path with Maximum Gold
```java
class Solution {
    private int getMaxGold(int[][] grid, int row, int col, boolean[][] visited) {
        int m = grid.length;
        int n = grid[0].length;
        if (row < 0 || row >= m || col < 0 || col >= n || 
        visited[row][col] || grid[row][col] == 0) {
            return 0;
        }
        visited[row][col] = true;
        int left = getMaxGold(grid, row, col - 1, visited);
        int right = getMaxGold(grid, row, col + 1, visited);
        int up = getMaxGold(grid, row - 1, col, visited);
        int down = getMaxGold(grid, row + 1, col, visited);
        visited[row][col] = false;
        return grid[row][col] + Math.max(Math.max(left, right), Math.max(up, down));
    }

    public int getMaximumGold(int[][] grid) {
        int maxGold = 0;
        int m = grid.length;
        int n = grid[0].length;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] != 0) {
                    boolean[][] visited = new boolean[m][n];
                    maxGold = Math.max(maxGold, getMaxGold(grid, i, j, visited));
                }
            }
        }
        return maxGold;
    }
}
