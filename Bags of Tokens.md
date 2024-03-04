# March-4
## 948. Bags of Tokens
```java
class Solution {
    public int bagOfTokensScore(int[] tokens, int power) {
        Arrays.sort(tokens);
        int i=0,j=tokens.length-1;
        int ans=0,max=0;
        while(i<=j)
        {
            if(power>=tokens[i])
            {
                ans++;
                max=Math.max(ans,max);
                power-=tokens[i];
                i++;
            }
            else if(ans>0)
            {
                power+=tokens[j];
                ans--;
                j--;
            }else break;
        }return max;
    }
}
