# August-6
## Minimum Number of Pushes to Type Word II
```java
import java.util.Arrays;
import java.util.Comparator;
class Solution {
    public int minimumPushes(String word) {
        int[] alphaCount = new int[26];
        for (char ch : word.toCharArray()) {
            alphaCount[ch - 'a']++;
        }
        Integer[] alphaCountObj = Arrays.stream(alphaCount).boxed().toArray(Integer[]::new);
        Arrays.sort(alphaCountObj, new Comparator<Integer>() {
            public int compare(Integer a, Integer b) {
                return b - a;
            }
        });
        int distinct = 0, ans = 0;
        for (int count : alphaCountObj) {
            if (count > 0) {
                ans += (count * (1 + distinct / 8));
                distinct++;
            }
        }
        return ans;
    }
}
