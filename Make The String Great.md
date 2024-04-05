# April-5
##  1544. Make The String Great
```java
class Solution {
    public String makeGood(String s) {
        StringBuilder str=new StringBuilder("");
        str.append(s.charAt(0));
        for(int i=1;i<s.length();i++)
        {
            if(str.length()>0&&Math.abs((int)s.charAt(i)-(int)str.charAt(str.length()-1))==32)
             str.deleteCharAt(str.length()-1);
            else str.append(s.charAt(i)); 
        }return str.toString();
    }
}
