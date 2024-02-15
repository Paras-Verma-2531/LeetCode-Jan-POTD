# Febuary-15

## 2971. Find Polygon With the Largest Perimeter

```java
class Solution {
    public long largestPerimeter(int[] nums) {
        if(nums.length<3)return -1;
        Arrays.sort(nums);
        long sum=0;
        for(int i:nums)sum+=i;
        for(int i=nums.length-1;i>=0;i--)
        {
            sum-=nums[i];
            if(sum>nums[i])return sum+nums[i];
        }return -1;
    }
}
