# July-11
## 1190. Reverse Substring Between Each Parenthesis Pairs
```java
class Solution {
    private void reverse(char[]arr,int start,int end)
    {
        while(start<=end)
        {
            char temp=arr[start];
            arr[start++]=arr[end];
            arr[end--]=temp;
        }
    }
    public String reverseParentheses(String s) {
        Stack<Integer>stack=new Stack<>();
        char[]strArr=s.toCharArray();
        for(int i=0;i<s.length();i++)
        {
            char ch=s.charAt(i);
           if(ch=='(')stack.push(i);
           else if(ch==')')
           {
            int end=i-1;
            int start=stack.pop()+1;
            reverse(strArr,start,end);
           }
        }
        StringBuilder str=new StringBuilder();
        for(char ch:strArr)
        {
            if(ch=='('||ch==')')continue;
            str.append(ch);
        }return str.toString();
    }
}
