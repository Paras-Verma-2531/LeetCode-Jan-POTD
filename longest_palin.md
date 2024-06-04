# June-4
## 409. Longest Palindrome
```java
class Solution {
    public int longestPalindrome(String s) {
        Map<Character,Integer>map=new HashMap<>();
        boolean oddLength=false;
        for(char ch:s.toCharArray())map.put(ch,map.getOrDefault(ch,0)+1);
        int ans=0;
        for(char ch:map.keySet())
        {
            int freq=map.get(ch);
            if(freq%2==0)ans+=freq;
            else 
            {
                oddLength=true;
                ans+=freq-1;
            }
        }return oddLength? ans+1:ans;
    }
}
