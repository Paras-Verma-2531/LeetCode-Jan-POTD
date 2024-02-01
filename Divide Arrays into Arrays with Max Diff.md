# Febuary 1

## 2966. Divide Arrays into Arrays with Max Diff

```java
class Solution {
    private boolean isDiffValid(int[]arr,int start,int end,int diff)
    {
        return (arr[end-1]-arr[start])<=diff;
    }
    public int[][] divideArray(int[] nums, int k) {
        int[][]ans=new int[nums.length/3][3];
        Arrays.sort(nums);
        int i=0,start=0,end=3;
        int size=nums.length/3;
        while(size--!=0)
        {
            if(isDiffValid(nums,start,end,k))
            {
                ans[i++]=Arrays.copyOfRange(nums,start,end);
                start=end;
                end=end+3;
            }
            else return new int[0][0];
        }return ans;

    }
}
