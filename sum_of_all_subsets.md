# May-20
## 1863. Sum of All Subset XOR total
```java
class Solution {
    private int subsetXORSum(int[]arr,int ind,int xor)
    {
        if(ind==arr.length)return xor;
        int pick=subsetXORSum(arr,ind+1,xor^arr[ind]);
        int notpick=subsetXORSum(arr,ind+1,xor);
        return pick+notpick;
    }
    public int subsetXORSum(int[] nums) {
        return subsetXORSum(nums,0,0);
    }
}
