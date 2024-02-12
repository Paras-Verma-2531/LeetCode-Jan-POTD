# Febuary-12

## 169. Majority Element

```java
class Solution {
    public int majorityElement(int[] nums) {
        int majEle=nums[0];
        int count=1;
        for(int i=1;i<nums.length;i++)
        {
            if(nums[i]==majEle)count++;
            else count--;
            if(count==0)
            {
                count=1;
                majEle=nums[i];
            }
        }count=0;
        for(int ele:nums)
        {
            if(ele==majEle)count++;
        }
        if(count>nums.length/2)return majEle;
        return -1;
    }
}
