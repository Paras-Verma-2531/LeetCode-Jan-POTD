# Febuary-6

## 49. Group Anaggrams

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String,List<String>>map=new HashMap<>();
        for(String st:strs)
        {
            char[]chr=st.toCharArray();
            Arrays.sort(chr);
            String sorted=String.valueOf(chr);
            List<String>list=map.getOrDefault(sorted,
             new ArrayList<String>());
            list.add(st);
            map.put(sorted,list);

        }
        return new ArrayList<>(map.values());
    }
}
