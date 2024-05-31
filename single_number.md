# May-31
## 260. Single Number III
```java
class Solution {
    public int[] singleNumber(int[] nums) {
        int n = nums.length;
        if (n == 2) return nums;
        int xor = 0;
        for (int num : nums) {
            xor ^= num;
        }
        int rightmostSetBit = xor & (-xor);
        int ele1 = 0, ele2 = 0;
        for (int num : nums) {
            if ((num & rightmostSetBit) != 0) {
                ele1 ^= num;
            } else {
                ele2 ^= num;
            }
        }
        return new int[]{ele1, ele2};
    }
}
