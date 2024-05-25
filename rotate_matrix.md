# May-25
## Rotate Matrix
```java
class Solution {
    // transpose
    private void transpose(int[][]matrix)
    {
        for(int i=0;i<matrix.length;i++)
        {
            for(int j=0;j<i;j++)
            {
                int temp=matrix[i][j];
                matrix[i][j]=matrix[j][i];
                matrix[j][i]=temp;
            }
        }
    }
    private void reverse(int[][]arr)
    {
        for(int []temp:arr)reverse(temp);
    }
    private void reverse(int[]arr)
    {
        int i=0,j=arr.length-1;
        while(i<=j)
        {
            int temp=arr[i];
            arr[i++]=arr[j];
            arr[j--]=temp;
        }
    }
    public void rotate(int[][] matrix) {
        transpose(matrix);
        reverse(matrix);
    }
}
