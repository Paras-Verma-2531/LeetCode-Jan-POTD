# July-3
## 1509. Minimum Differences between smallest and largest
```java
class Solution {
    public int minDifference(int[] nums) {
        int n=nums.length;
        if(n<=4)return 0;
        Arrays.sort(nums);
        int minDiff=Integer.MAX_VALUE;
        int j=n-4;
        for(int i=0;i<4;i++)
        {
          minDiff=Math.min(minDiff,nums[j]-nums[i]);
          j++;
        }return minDiff;
    }
}
