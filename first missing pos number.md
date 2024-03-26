# March-26
## 41. Find the first missing positive number
```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int k=1;
        Arrays.sort(nums);
        for(int i=0;i<nums.length;i++)
        {
            if(nums[i]<=0||i>0&&nums[i]==nums[i-1])continue;
            else if(nums[i]<=k)k++;
            else return k;
        }return k;
    }
}
