# September-1
## 2022. Convert 1D Array into 2D Array
```java
class Solution {
    public int[][] construct2DArray(int[] original, int m, int n) {
        int[][]ans=new int[m][n];
        if(m*n < original.length|| m*n >original.length ) return new int[0][0];
        for(int i=0;i<original.length;i++)
        {
            int row=i/n;
            int col=i%n;
            ans[row][col]=original[i];
        }return ans;
    }
}
