# Febuary-20

## 268. Missing Number

```java
class Solution {
    private void swap(int[]arr,int i,int j)
    {
        int temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
    }
    public int missingNumber(int[] nums) {
        int n=nums.length,i=0;
        while(i<n)
        {
            int actIndex=nums[i];
            if(actIndex<n&&nums[actIndex]!=nums[i])swap(nums,i,actIndex);
            else i++;
        }
        for(i=0;i<n;i++)
        {
            if(nums[i]!=i)return i;
        }return n;
    }
}
