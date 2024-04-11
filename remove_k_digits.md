# April-11
## 402. Remove K Digits
```java
class Solution {
    public String removeKdigits(String num, int k) {
        Stack<Character>stack=new Stack<>();
        if(num.length()==k)return "0";
        //form the monotonic stack
        for(int i=0;i<num.length();i++)
        {
            if(stack.isEmpty())stack.push(num.charAt(i));
            else
            {
                int val=num.charAt(i)-'0';
                while(!stack.isEmpty()&&k>0&&val<stack.peek()-'0')
                {
                    stack.pop();
                    k--;
                }stack.push(num.charAt(i));
            }
        }// if k> 0 pop out, k elements
        while(k>0)
        {
            stack.pop();
            k--;
        }
        String ans="";
        while(!stack.isEmpty())ans=stack.pop()+ans;
        int i=0;
        //remove the leading zeros
        while(i<ans.length()&&ans.charAt(i)=='0')i++;
        return i>=ans.length()?"0":ans.substring(i);
    }
}
