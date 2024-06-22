# June-22
## 1248. Count Number of Nice Subarrays
```java
class Solution {
    private int slidingWindowAtMost(int[]nums,int k)
    {
        int i=0,j=0,ans=0,count=0;
        while(j<nums.length)
        {
            if(nums[j]%2!=0)count++;
            while(i<=j&&count>k)
            {
                if(nums[i]%2!=0)count--;
                i++;
            }if(count<=k)ans+=j-i+1;
            j++;
        }return ans;
    }
    public int numberOfSubarrays(int[] nums, int k) {
        return slidingWindowAtMost(nums,k)-slidingWindowAtMost(nums,k-1);
    }
}
