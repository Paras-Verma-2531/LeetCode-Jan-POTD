# January-25 

## 1143. Longest Common Subsequence

```java
class Solution {
   private int longestCommonSubsequence(String st1, String st2,
   int len1,int len2,int[][]dp) {
        if(len1==st1.length()||len2==st2.length())return 0;
        if(dp[len1][len2]!=-1)return dp[len1][len2];
        if(st1.charAt(len1)==st2.charAt(len2))return 
        dp[len1][len2]=1+longestCommonSubsequence(st1,st2,len1+1,len2+1,dp);
        return dp[len1][len2]=Math.max(longestCommonSubsequence(st1,st2,
        len1+1,len2,dp),
        longestCommonSubsequence(st1,st2,len1,len2+1,dp));
    }
    public int longestCommonSubsequence(String text1, String text2) {
        int[][]dp=new int[text1.length()][text2.length()];
        for(int[]arr:dp)Arrays.fill(arr,-1);
        return longestCommonSubsequence(text1,text2,0,0,dp);
    }
}
