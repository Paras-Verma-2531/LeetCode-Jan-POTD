# Aug-3
##1460. Make Two Arrays Equal by Reverse
```java
class Solution {
    public boolean canBeEqual(int[] target, int[] arr) {
        if(target.length!=arr.length)return false;
        Map<Integer,Integer>map=new HashMap<>();
        for(int ele:target)map.put(ele,map.getOrDefault(ele,0)+1);
        for(int ele:arr)
        {
            if(!map.containsKey(ele))return false;
            map.put(ele,map.get(ele)-1);
            if(map.get(ele)==0)map.remove(ele);
        }
        return map.size()==0;
    }
}
