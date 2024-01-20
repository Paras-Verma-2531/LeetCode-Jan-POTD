# January-20

## 907.Sum of Subarray Minimums.

```java
class Solution {
    public int sumSubarrayMins(int[] arr) {
        Stack<Integer> stack = new Stack<>();
        int[] left = new int[arr.length];
        int[] right = new int[arr.length];

        // Fill the left array [first smaller indices to the left]
        for (int i = 0; i < arr.length; i++) {
            while (!stack.isEmpty() && arr[i] < arr[stack.peek()]) stack.pop();
            left[i] = stack.isEmpty() ? -1 : stack.peek();
            stack.push(i);
        }

        // Fill the right array
        stack.clear();
        for (int i = arr.length - 1; i >= 0; i--) {
            while (!stack.isEmpty() && arr[i] <= arr[stack.peek()]) stack.pop();
            right[i] = stack.isEmpty() ? arr.length : stack.peek();
            stack.push(i);
        }

        int ans = 0;
        int mod = 1000000007;

        for (int i = 0; i < arr.length; i++) {
            long k = (i - left[i]) * (right[i] - i);
            ans += (arr[i] * k) % mod;
            ans %= mod;
        }

        return ans;
    }
}
