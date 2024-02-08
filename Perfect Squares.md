# Febuary-8

## 279. Perfect Squares.

```java
class Solution {
    private int helper(int num,int[]dp)
    {
        if(num<=0)return 0;
        if(dp[num]!=-1)return dp[num];
        int ans=num;
        for(int i=1;i*i<=num;i++)
        {
            dp[num]=ans=Math.min(ans,1+helper(num-i*i,dp));
        }return ans;
    }
    public int numSquares(int n) {
        int[]dp=new int[n+1];
        Arrays.fill(dp,-1);
        return helper(n,dp);

    }
}
