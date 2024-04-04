# April-4
## 1614. Maximum Nesting Depth of the VPS
```java
class Solution {
    public int maxDepth(String s) {
        int count=0,max=0;
        for(char ch:s.toCharArray())
        {
            if(ch=='(')count++;
            else if(ch==')')count--;
            max=Math.max(max,count);
        }return max;
    }
}
