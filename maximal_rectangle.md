# April-13
## 85. Maximal Rectangle
```java
class Solution {
    private int[] previousSmaller(int[] arr)
    {
        int[] ans=new int[arr.length];
        Stack<Integer>stack=new Stack<>();
        for(int i=0;i<arr.length;i++)
        {
            while(!stack.isEmpty()&&arr[stack.peek()]>=arr[i])
                stack.pop();
            ans[i]=stack.isEmpty()?-1:stack.peek();
            stack.push(i);
        }return ans;
    }
    private int[] nextSmaller(int[] arr)
    {
        int[] ans=new int[arr.length];
        Stack<Integer>stack=new Stack<>();
        for(int i=arr.length-1;i>=0;i--)
        {
            while(!stack.isEmpty()&&arr[stack.peek()]>=arr[i])
                stack.pop();
            ans[i]=stack.isEmpty()?arr.length:stack.peek();
            stack.push(i);
        }return ans;
    }
    private int largestRectangleArea(int[] heights) {
        int maxsum=0;
        int [] ps=previousSmaller(heights);
        int [] ns=nextSmaller(heights);
        for(int i=0;i<heights.length;i++)
        {
            int cur=(ns[i]-ps[i]-1)*heights[i];
            maxsum=Math.max(maxsum,cur);
        }return maxsum;
        
    }
    public int maximalRectangle(char[][] matrix) {
        int[][]ans=new int[matrix.length][matrix[0].length];
        int m=matrix.length;
        int n=matrix[0].length;
        for(int i=0;i<n;i++)ans[0][i]=matrix[0][i]=='1'?1:0;
        // build the histogram
        for(int i=1;i<m;i++)
        {
            for(int j=0;j<n;j++)
            {
                ans[i][j]=matrix[i][j]=='0'?0:1+ans[i-1][j];
            }
        }
        int maxArea=0;
        for(int[]arr:ans)
        {
            maxArea=Math.max(maxArea,largestRectangleArea(arr));
        }return maxArea;
        
    }
}
