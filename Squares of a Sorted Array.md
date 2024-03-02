# March-2
## 977.Squares of a Sorted Array
```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int[]ans=new int[nums.length];
        int k=ans.length-1;
        int i=0,j=k;
        while(i<=j)
        {
            if(nums[i]*nums[i] < nums[j]*nums[j])
            {
                ans[k--]=nums[j]*nums[j];
                j--;
            }
            else
            {
                ans[k--]=nums[i]*nums[i];
                i++;
            }
        }return ans;
    }
}
