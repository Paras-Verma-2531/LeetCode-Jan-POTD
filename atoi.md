# June-30
## 8. String to Integer (atoi)
```java
public int myAtoi(String s) {
        StringBuilder temp=new StringBuilder();
        int i=0,ans=0;
        boolean sign=true;
        if(s.length()==0)return 0;
        if(Character.isLetter(s.charAt(0)))return 0;
        while(i<s.length()&&s.charAt(i)==' ')i++;
        if(i<s.length()&&s.charAt(i)=='-')
        {
            i++;
            sign=false;
        }
        else if(i<s.length()&&s.charAt(i)=='+')
        {
            i++;
            sign=true;
        }
        while(i<s.length()&&Character.isDigit(s.charAt(i)))
        {
            int num=s.charAt(i)-'0';
            if (ans > (Integer.MAX_VALUE - num) / 10) {
                return (sign==true) ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }
            ans=ans*10 + num;
            i++;
        }
        return sign==false?ans*-1:ans;
        
    }
