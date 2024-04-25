# April-25
## 2370. Longest Ideal Subsequence
```java
class Solution {
    private int longestIdealString(String s,int[][]dp,int ind,char last,int k)
    {
        if(ind==s.length())return 0;
        if(dp[ind][last-'a']!=-1)return dp[ind][last-'a'];
        int pick=0;
        if(last=='{'||Math.abs(last-s.charAt(ind))<=k)
        {
            pick=1+longestIdealString(s,dp,ind+1,s.charAt(ind),k);
        }
        int notPick=longestIdealString(s,dp,ind+1,last,k);
        return dp[ind][last-'a']=Math.max(pick,notPick);
    }
    public int longestIdealString(String s, int k) {
        int[][]dp=new int[s.length()][27];
        for(int[]arr:dp)Arrays.fill(arr,-1);
        return longestIdealString(s,dp,0,'{',k);
    }
}
