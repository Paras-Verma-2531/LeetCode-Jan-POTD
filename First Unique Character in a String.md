# Febuary 5

## 387. First Unique Character in a String

```java
class Solution {
    public int firstUniqChar(String s) {
        int[]arr=new int[26];
        char[]chr=s.toCharArray();
        for(char ch:chr)arr[ch-'a']++;
        int i=0;
        for(char ch:chr)
        {
            int temp=arr[ch-'a'];
            if(temp-1==0)return i;
            i++;
        }return -1;
    }
}
