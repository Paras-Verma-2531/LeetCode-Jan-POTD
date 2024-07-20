# July-20
## 1605. Find Valid Matrix Given Row and Col Sum
```java
class Solution {
    private long currSum(int[][]ans,int col)
    {
        long sum=0;
        for(int i=0;i<ans.length;i++)sum+=ans[i][col];
        return sum;
    }
    public int[][] restoreMatrix(int[] rowSum, int[] colSum) {
     int[][]ans=new int[rowSum.length][colSum.length];
     //set the initial sum of ans as rowSum
     for(int i=0;i<rowSum.length;i++)ans[i][0]=rowSum[i];
     for(int i=0;i<colSum.length-1;i++)
     {
        long actSum=colSum[i];
        long curr=currSum(ans,i);
        long extra=curr-actSum;
        for(int row=0;row<ans.length;row++)
        {
            long deficit=Math.min(extra,ans[row][i]);
            ans[row][i]=(int)(ans[row][i]-deficit);
            ans[row][i+1]=(int)deficit;
            extra-=deficit;
        }
     }return ans;
    }
}
