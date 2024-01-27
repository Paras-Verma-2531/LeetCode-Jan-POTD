# January-27

## 629. K Inverse Pairs Array

```java
class Solution {
    private int inverseHelper(int n,int k,int[][]dp)
    {
        if(n==0)return 0;
        if(k==0)return 1;
        if(dp[n][k]!=-1)return dp[n][k];
        int count=0;
        for(int i=0;i<=Math.min(n-1,k);i++)
        {
            count+=inverseHelper(n-1,k-i,dp);
            count%=1000000007;
        }return dp[n][k]=count;
    }
    public int kInversePairs(int n, int k) {
        int[][]dp=new int[n+1][k+1];
        for(int []arr:dp)Arrays.fill(arr,-1);
        return inverseHelper(n,k,dp);
    }
}
