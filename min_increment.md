# June-14
## 945. Minimum Increment to Make Array Unique
```java
class Solution {
    public int minIncrementForUnique(int[] arr) {
        Arrays.sort(arr);
        int minInc=0;
        int n=arr.length;
        for(int i=1;i<n;i++)
        {
            if(arr[i]>arr[i-1])continue;
            int stepsReq=(arr[i-1]+1)-arr[i];
            arr[i]+=stepsReq;
            minInc+=stepsReq;
        }return minInc;
    }
}
