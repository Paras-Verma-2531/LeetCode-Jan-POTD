# July-19
## 1380. Lucky Numbers in Matrix
```java
class Solution {
    private boolean isRowMin(int[][]arr,int row,int ele)
    {
       int min=ele;
       for(int i=0;i<arr[0].length;i++)min=Math.min(min,arr[row][i]);
       return min==ele;
    }
    private boolean isColMax(int[][]arr,int col,int ele)
    {
        int max=ele;
       for(int i=0;i<arr.length;i++)max=Math.max(max,arr[i][col]);
       return max==ele;
    }
    public List<Integer> luckyNumbers (int[][] matrix) {
        List<Integer>magicNumbers=new ArrayList<>();
       for(int row=0;row<matrix.length;row++)
       {
        for(int col=0;col<matrix[0].length;col++)
        {
            if(isRowMin(matrix,row,matrix[row][col])&&
             isColMax(matrix,col,matrix[row][col]) )
              magicNumbers.add(matrix[row][col]);
        }
       }return magicNumbers;
    }
}
