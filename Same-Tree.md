# January-5 

## 300. Longest Increasing Subsequence

```java
private int helper(int[]arr,int ind,int prev_ind,int[][]dp)
    {
        if(ind==arr.length)return 0;
        if(dp[ind][prev_ind+1]!=-1)return dp[ind][prev_ind+1];
        int pick=0;
        if(prev_ind==-1||arr[ind]>arr[prev_ind])pick=1+helper(arr,ind+1,ind,dp);
        int notpick=0+helper(arr,ind+1,prev_ind,dp);
        return dp[ind][prev_ind+1]=Math.max(pick,notpick);
    }
    public int lengthOfLIS(int[] nums) {
        int[][]dp=new int[nums.length][nums.length+1];
        for(int[]arr:dp)Arrays.fill(arr,-1);
        return helper(nums,0,-1,dp);
    }
