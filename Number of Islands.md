# April-19
## 200. Number of Islands
```java
class Solution {
    private void dfs(char[][]grid,boolean[][]vis,int row,int col)
    {
        if(row<0||row>=grid.length||col<0||col>=grid[0].length||grid[row][col]=='0'||
        vis[row][col]==true)return;
        vis[row][col]=true;
        dfs(grid,vis,row,col-1);
        dfs(grid,vis,row-1,col);
        dfs(grid,vis,row,col+1);
        dfs(grid,vis,row+1,col);
    }
    public int numIslands(char[][] grid) {
        int m=grid.length,n=grid[0].length;
        boolean[][]vis=new boolean[m][n];
        int count=0;
        for(int i=0;i<m;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(grid[i][j]=='1'&& vis[i][j]==false)
                {
                    count++;
                    dfs(grid,vis,i,j);
                }
            }
        }return count;
    }
}
