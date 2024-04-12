# April-12
## 42. Trapping Rain Water
```java
class Solution {
    public int trap(int[] height) {
        int n=height.length;
        int[]left=new int[n];
        int[]right=new int[n];
        int max=0;
        for(int i=0;i<n;i++)
        {
            if(height[i]>max)max=height[i];
            left[i]=max;
        }
        System.out.println(Arrays.toString(left));
        //calculate the first right max;
        max=0;
        for(int i=n-1;i>=0;i--)
        {
           if(height[i]>max)max=height[i];
           right[i]=max;
        }
        System.out.println(Arrays.toString(right));
        //cal the sum
        int sum=0;
        for(int i=0;i<n;i++)
        {
            sum+=Math.min(left[i],right[i])-height[i];
        }return sum;
    }
}
