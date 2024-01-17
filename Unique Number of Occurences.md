# January-17

## 1207. Unique Number of Occurences.

```java
class Solution {
    public boolean uniqueOccurrences(int[] arr) {
        Map<Integer,Integer>map=new HashMap<>();
        Set<Integer>set=new HashSet<>();
        for(int i:arr)
        {
            map.put(i,map.getOrDefault(i,0)+1);
        }
        for(int key:map.keySet())
        {
            int freq=map.get(key);
            if(set.contains(freq))return false;
            set.add(freq);
        }return true;
    }
}
