# January-21

## 198. House Robber

```java
class Solution {
//memoization
    private int rob(int[]arr,int ind,int[]dp)
    {
        if(ind==0)return arr[0];
        if(ind<0)return 0;
        if(dp[ind]!=-1)return dp[ind];
        int pick=arr[ind]+rob(arr,ind-2,dp);
        int notPick=rob(arr,ind-1,dp);
        return dp[ind]=Math.max(pick,notPick);
    }
    public int rob(int[] nums) {
//tabulation
        int[]dp=new int[nums.length];
        dp[0]=nums[0];
        for(int i=1;i<nums.length;i++)
        {
            int pick=nums[i];
            if(i-2>=0)pick+=dp[i-2];
            int notPick=dp[i-1];
            dp[i]=Math.max(pick,notPick);
        }return dp[nums.length-1];
    }
}
