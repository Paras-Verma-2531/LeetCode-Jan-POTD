# May-12
## 2375. Largest Local Value in Matrix
```java
class Solution {
    private int findMax(int[][] grid, int x, int y) {
        int maxElement = 0;
        for (int i = x; i < x + 3; i++) {
            for (int j = y; j < y + 3; j++) {
                maxElement = Math.max(maxElement, grid[i][j]);
            }
        }
        return maxElement;
    }
    
    public int[][] largestLocal(int[][] grid) {
        int N = grid.length;
        
        int[][] maxLocal = new int[N - 2][N - 2];
        for (int i = 0; i < N - 2; i++) {
            for (int j = 0; j < N - 2; j++) {
                maxLocal[i][j] = findMax(grid, i, j);
            }
        }return maxLocal;
    }
}
