# April-6
## 1249. Minimum Remove to make Valid Parenthesis
```java
class Solution {
    public String minRemoveToMakeValid(String s) {
        int openParenCount=0;
        char[]chr=s.toCharArray();
        for(int i=0;i<chr.length;i++)
        {
            if(chr[i]=='(')openParenCount++;
            else if(chr[i]==')')
            {
                if(openParenCount>0)openParenCount--;
                else chr[i]='!';
            }
        }
        int closeParenCount=0;
        for(int i=chr.length-1;i>=0;i--)
        {
            if(chr[i]==')')closeParenCount++;
            else if(chr[i]=='(')
            {
                if(closeParenCount>0)closeParenCount--;
                else chr[i]='!';
            }
        }
        String ans="";
        for(char ch:chr)
        {
            if(ch=='!')continue;
            ans+=ch;
        }return ans;
    }
}
