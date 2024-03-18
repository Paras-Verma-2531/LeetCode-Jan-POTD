# March-19
## 452. Minimum Arrows to Burst ballons
```java
class Solution {
    public int findMinArrowShots(int[][] points) {
        Arrays.sort(points, Comparator.comparingLong(a -> a[0]));
        int arrows=1;
        long end=points[0][1];
        for (int i = 1; i < points.length; i++) {
            // If the next balloon overlaps with the current arrow
            if (points[i][0] <= end) {
                // Update the end position of the arrow
                end = Math.min(end, points[i][1]);
            } else {
                // Balloon doesn't overlap with the current arrow, shoot a new arrow
                arrows++;
                end = points[i][1];
            }
        }
        return arrows;
    }
}
