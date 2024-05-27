# May-27
## 1608. Special Array with X elements
```java
class Solution {
    private int getCount(int[]arr,int ele)
    {
        int count=0;
        for(int item:arr)if(item>=ele)count++;
        return count;
    }
    public int specialArray(int[] nums) {
        for(int i=0;i<=nums.length;i++)
        {
            if(getCount(nums,i)==i)return i;
        }return -1;
    }
}
