# June-1
## Score of a String 
```java
class Solution {
    public int scoreOfString(String s) {
        int score=0;
        for(int i=0;i<s.length()-1;i++)
        {
            int val1=s.charAt(i)-'a';
            int val2=s.charAt(i+1)-'a';
            score+=Math.abs(val1-val2);
        }return score;
    }
}
