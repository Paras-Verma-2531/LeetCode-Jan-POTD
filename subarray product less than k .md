# March-27
## 713. SubArray Product less than K 
```java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        if (k <= 1) return 0;  
        int i=0,j=0,count=0,n=nums.length;
        int product=1;
        while(j<n)
        {
            product*=nums[j];
            while(i<n&&product>=k)
            {
                product/=nums[i];
                i++;
            }if(product<k)count+=j-i+1;
            j++;
        }return count;
    }
}
