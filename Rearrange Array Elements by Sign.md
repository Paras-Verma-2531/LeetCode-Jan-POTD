# Febuary-14

## 2149. Rearrange Array Elements by Sign

```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int[]pos=new int[nums.length/2];
        int []neg=new int[nums.length/2];
        int i=0,j=0;
        for(int item:nums)
        {
            if(item>=0)pos[i++]=item;
            else neg[j++]=item;
            
        }
        for(int k=0;k<nums.length/2;k++)
        {
            nums[2*k]=pos[k];
            nums[2*k+1]=neg[k];
        }
        return nums;
    }
}
