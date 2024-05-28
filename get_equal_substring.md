# May-28
## 1208. Get Equal Substrings within Budget
```java
class Solution {
    public int equalSubstring(String s, String t, int maxCost) {
        int i=0,j=0,n=s.length();
        int maxLen=0;
        int cost=0;
        while(j<n)
        {
            cost+=Math.abs(s.charAt(j)-t.charAt(j));
            while(cost>maxCost)
            {
                cost-=Math.abs(s.charAt(i)-t.charAt(i));
                i++;
            }maxLen=Math.max(maxLen,j-i+1);
            j++;
        }return maxLen;
    }
}
