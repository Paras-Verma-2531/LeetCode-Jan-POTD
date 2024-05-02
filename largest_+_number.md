# May-2
## Largest + Number That Exists
```java
class Solution {
    public int findMaxK(int[] nums) {
        Set<Integer>set=new HashSet<>();
        int ans=-1;
        for(int num:nums)
        {
            set.add(num);
            if(set.contains(-num))ans=Math.max(ans,Math.abs(num));
        }return ans;
    }
}
