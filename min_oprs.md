# April-29
## 2997. Minimum Number of Operations to Make Array Xor Equals K
```java
class Solution {
    public int minOperations(int[] nums, int k) {
        int xor=0;
        for(int ele:nums)xor^=ele;
        int diffBits=xor^k;
        int count=0;
        while(diffBits!=0)
        {
            diffBits&=(diffBits-1);
            count++;
        }return count;
    }
}
