# Febuary-9

## 368. Largest Divisible Subset

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public List<Integer> largestDivisibleSubset(int[] nums) {
        if (nums == null || nums.length == 0) {
            return new ArrayList<>();
        }
        int n = nums.length;
        Arrays.sort(nums);
        int[] dp = new int[n];
        Arrays.fill(dp, 1);
        int maxSubsetSize = 1;
        int maxSubsetIndex = 0;
        for (int i = 1; i < n; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] % nums[j] == 0 && dp[i] < dp[j] + 1) {
                    dp[i] = dp[j] + 1;
                    if (dp[i] > maxSubsetSize) {
                        maxSubsetSize = dp[i];
                        maxSubsetIndex = i;
                    }
                }
            }
        }
        List<Integer> result = new ArrayList<>();
        int currentSize = maxSubsetSize;
        int currentElement = nums[maxSubsetIndex];

        for (int i = maxSubsetIndex; i >= 0; i--) {
            if (currentElement % nums[i] == 0 && dp[i] == currentSize) {
                result.add(nums[i]);
                currentElement = nums[i];
                currentSize--;
            }
        }
        return result;
    }
}
