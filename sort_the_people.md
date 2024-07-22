# July-22
## 2418. Sort the People
```java
class Solution {
    public String[] sortPeople(String[] names, int[] heights) {
        String sortedNames[]=new String[names.length];
        Map<Integer, String> map = new TreeMap<>(new Comparator<Integer>() {
            public int compare(Integer a, Integer b) {
                return b - a;
            }
        });
        for(int i=0;i<names.length;i++)map.put(heights[i],names[i]);
        int i=0;
        for(int key:map.keySet())
        {
            sortedNames[i++]=map.get(key);
        }return sortedNames;
    }
}
