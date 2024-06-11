# June-11
## 1122. Relative Sort Order
```java
class Solution {
    public int[] relativeSortArray(int[] arr1, int[] arr2) {
        Map<Integer,Integer>map=new TreeMap<>();
        for(int ele:arr1)map.put(ele,map.getOrDefault(ele,0)+1);
        int i=0;
        for(int item:arr2)
        {
            int count=map.get(item);
            Arrays.fill(arr1,i,i+count,item);
            i+=count;
            map.put(item,0);
        }
        for(int key:map.keySet())
        {
            if(map.get(key)>0)
            {
                int count=map.get(key);
                Arrays.fill(arr1,i,i+count,key);
                i+=count;
            }
        }
        return arr1;
    }
}
