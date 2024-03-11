# March-11
## 791. Custom Sort String
```java
class Solution {
    public String customSortString(String order, String s) {
        Map<Character,Integer>map=new HashMap<>();
        for(char ch:s.toCharArray())map.put(ch,map.getOrDefault(ch,0)+1);
        StringBuilder str=new StringBuilder();
        for(char ch:order.toCharArray())
        {
            if(map.containsKey(ch))
            {
               while(map.get(ch)>0)
               {
                   str.append(ch);
                   map.put(ch,map.get(ch)-1);
               }
            }
        }
        for(char key:map.keySet())
        {
            while(map.get(key)>0)
            {
                str.append(key);
                map.put(key,map.get(key)-1);
            }
        }return str.toString();
    }
}
