# March-8
## 3005. Count Elements With Maximum Frequencies
```java
class Solution {
    public int maxFrequencyElements(int[] nums) {
        int[]arr=new int[101];
        int maxFreq=0,count=0;
        for(int i:nums)
        {
            arr[i]++;
            maxFreq=Math.max(maxFreq,arr[i]);
        }
        for(int i:arr)if(i==maxFreq)count++;
        return count*maxFreq;
    }
}
