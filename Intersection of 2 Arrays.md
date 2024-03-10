# March-10
## 349. Intersection of 2 Arrays
```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Map<Integer,Boolean>map=new HashMap<>();
        for(int i:nums1)map.put(i,false);
        int count=0;
        for(int i:nums2)
        {
            if(map.containsKey(i)&&map.get(i)==false)
            {
                map.put(i,true);
                count++;
            }
        }
        int[]ans=new int[count];
        int p=0;
        for(int key:map.keySet())if(map.get(key)==true)ans[p++]=key;
        return ans;
    }
}
