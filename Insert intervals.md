# March-17
## 57. Insert Intervals
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        List<List<Integer>> ans = new ArrayList<>();
        int i = 0;
        int n = intervals.length;
        while (i < n && intervals[i][1] < newInterval[0]) {
            ans.add(Arrays.asList(intervals[i][0], intervals[i][1]));
            i++;
        }
        while (i < n && intervals[i][0] <= newInterval[1]) {
            newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
            newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
            i++;
        }
        ans.add(Arrays.asList(newInterval[0], newInterval[1]));
        while (i < n) {
            ans.add(Arrays.asList(intervals[i][0], intervals[i][1]));
            i++;
        }
        int[][] result = new int[ans.size()][2];
        for (int j = 0; j < ans.size(); j++) {
            result[j][0] = ans.get(j).get(0);
            result[j][1] = ans.get(j).get(1);
        }

        return result;
    }
}
