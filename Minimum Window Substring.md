# Febuary 4

## 76. Minimum Window Substring

```java
class Solution {
    public String minWindow(String s, String t) {
     Map<Character,Integer>map=new HashMap<>();
     for(char chr:t.toCharArray())
      map.put(chr,map.getOrDefault(chr,0)+1);
     int count=map.size();
     int i=0,j=0;
     int start=-1;
     int minLen=Integer.MAX_VALUE;
     while(j<s.length())
     {
         char ch=s.charAt(j);
        if(map.containsKey(ch))
        {
            map.put(ch,map.get(ch)-1);
            if(map.get(ch)==0)count--;
        }
        while(count<=0)
        {
            char ch2=s.charAt(i);
            if(map.containsKey(ch2))
            {
                map.put(ch2,map.get(ch2)+1);
                if(map.get(ch2)==1)count++;
            }
            if(j-i+1<=minLen)
            {
                minLen=j-i+1;
                start=i;
            }
            i++;
        }
        j++;
     }
     if(minLen==Integer.MAX_VALUE)return "";
     return s.substring(start,start+minLen);
        
    }
}
