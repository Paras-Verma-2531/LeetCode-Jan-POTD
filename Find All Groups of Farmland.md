# April-20
## 1992. Find All Groups of Farmland
```java
class Solution {
    private void dfs(int[][] land, boolean[][] vis, int row, int col, int[] ans) {
        if (row < 0 || row >= land.length || col < 0 || col >= land[0].length || vis[row][col] == true
                || land[row][col] == 0)
            return;
        vis[row][col] = true;
        // Update top-left coordinates
        ans[0] = Math.min(ans[0], row);
        ans[1] = Math.min(ans[1], col);

        // Update bottom-right coordinates
        ans[2] = Math.max(ans[2], row);
        ans[3] = Math.max(ans[3], col);
        dfs(land, vis, row, col - 1, ans);
        dfs(land, vis, row - 1, col, ans);
        dfs(land, vis, row, col + 1, ans);
        dfs(land, vis, row + 1, col, ans);
    }

    public int[][] findFarmland(int[][] land) {
        int m = land.length, n = land[0].length;
        boolean[][] vis = new boolean[m][n];
        ArrayList<int[]> ans = new ArrayList<>();
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (land[i][j] == 1 && vis[i][j] == false) {
                    int[] arr = { i, j, i, j };
                    dfs(land, vis, i, j, arr);
                    ans.add(arr);
                }
            }
        }
        int size = ans.size();
        int i = 0;
        int[][] finalAns = new int[size][4];
        for (int[] arr : ans)
            finalAns[i++] = arr;
        return finalAns;
    }
}
