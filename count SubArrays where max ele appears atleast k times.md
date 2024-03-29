# March-29
## count SubArrays where max ele appears atleast k times
```java
class Solution {
    public long countSubarrays(int[] nums, int k) {
        long ans=0,count=0;
        int maxEle=0;
        for(int ele:nums)maxEle=Math.max(maxEle,ele);
        int l=0,r=0;
        while(r<nums.length)
        {
            if(nums[r]==maxEle)count++;
            while(count==k)
            {
                if(nums[l]==maxEle)count--;
                l++;
            }ans+=l;
            r++;
        }return ans;
    }
}
