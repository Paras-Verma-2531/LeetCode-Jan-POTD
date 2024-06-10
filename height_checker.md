# June-10
## 1051. Height Checker
```java
class Solution {
    public int heightChecker(int[] heights) {
      int[]expected=Arrays.copyOfRange(heights,0,heights.length);
      Arrays.sort(expected);
      int count=0;
      for(int i=0;i<heights.length;i++)
      {
        if(expected[i]!=heights[i])count++;
      }return count;  
    }
}
