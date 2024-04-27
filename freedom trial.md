# April-27
## 514. Freedom Trial
```java
class Solution {
    private int dis(int curr,int keyInd,String ring)
    {
        int clockWiseSteps=Math.abs(curr-keyInd);
        int antiClockWiseSteps=ring.length()-clockWiseSteps;
        return Math.min(clockWiseSteps,antiClockWiseSteps);
    }
    private int minSteps(String ring,String key,int[][]dp,int ringInd,int keyInd)
    {
        if(keyInd==key.length())return 0;
        if(dp[ringInd][keyInd]!=-1)return dp[ringInd][keyInd];
        int steps=Integer.MAX_VALUE;
        for(int i=0;i<ring.length();i++)
        {   
            if(ring.charAt(i)==key.charAt(keyInd))
            {
                int ans=1+dis(i,ringInd,ring)+minSteps(ring,key,dp,i,keyInd+1);
                steps=Math.min(steps,ans);
            }
        }return dp[ringInd][keyInd]=steps;
    }
    public int findRotateSteps(String ring, String key) {
        //if(ring.equals(key))return 2*ring.length()-1;
        int n=ring.length(),m=key.length();
        int[][]dp=new int[n][m];
        for(int[]arr:dp)Arrays.fill(arr,-1);
        return minSteps(ring,key,dp,0,0);
    }
}
