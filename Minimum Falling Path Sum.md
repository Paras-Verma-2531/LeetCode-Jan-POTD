# January-19

## 931. Minimum Falling Path Sum.

```java
class Solution {
//memoization
    private int minHelper(int row,int col,int[][]arr,int[][]dp)
    {
        if(row>=arr.length||col<0||col>=arr[0].length)return Integer.MAX_VALUE;
        if(row==arr.length-1)return arr[row][col];
        if(dp[row][col]!=-1)return dp[row][col];
        int next=minHelper(row+1,col,arr,dp);
        int left=minHelper(row+1,col-1,arr,dp);
        int right=minHelper(row+1,col+1,arr,dp);
        return dp[row][col]=arr[row][col]+Math.min(left,Math.min(next,right));
    }
    public int minFallingPathSum(int[][] matrix) {
        int m=matrix.length;
        int n=matrix[0].length;
        int[][]dp=new int[m+1][n+1];
//tabulation
       for(int col=0;col<n;col++)dp[m-1][col]=matrix[m-1][col];
       for(int i=n-2;i>=0;i--)
       {
           for(int j=0;j<n;j++)
           {
                int up=dp[i+1][j];
                int ld=Integer.MAX_VALUE;if(j-1>=0)ld=dp[i+1][j-1];
                int rd=Integer.MAX_VALUE;if(j+1<n)rd=dp[i+1][j+1];
                dp[i][j]=Math.min(up,Math.min(ld,rd))+matrix[i][j];
           }
       }int min=Integer.MAX_VALUE;
        for(int i=0;i<n;i++)min=Math.min(min,dp[0][i]);
        return min;
    }
}
