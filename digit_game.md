# July-28
## 3232. Find if Digit Game can be Won
```java
class Solution {
    public boolean canAliceWin(int[] nums) {
        int singleSum=0,doubleSum=0,totalSum=0;
        for(int num:nums)
        {
            if((int)Math.floor(Math.log10(num) + 1)==1)singleSum+=num;
            else doubleSum+=num;
            totalSum+=num;
        }
        //System.out.println(singleSum+" " +doubleSum +" " +totalSum);
        return doubleSum!=singleSum;
    }
}
