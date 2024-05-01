# May-1
## 2000. Reverse Prefix oof Word
```java
class Solution {
    public String reversePrefix(String word, char ch) {
        int index=word.indexOf(ch);
        if(index==-1||index==0)return word;
        String prefix=word.substring(0,index+1);
        StringBuilder str=new StringBuilder(prefix);
        str.reverse();
        return str.toString()+word.substring(index+1);
    }
}
