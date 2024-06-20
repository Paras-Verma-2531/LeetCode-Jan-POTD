# June-20
## 1552. Magnetic Force Between Two Balls
```java
class Solution {
 
   private boolean isPossible(int[]arr,int m,int minDis)
   {
     m--;
     int prev=0;
     for(int i=1;i<arr.length;i++)
     {
        if(Math.abs(arr[i]-arr[prev])>=minDis)
        {
            m--;
            prev=i;
        }
     }return m<=0;
   }
    public int maxDistance(int[] position, int m) {
        Arrays.sort(position);
        int n=position.length;
        int high=position[n-1]-position[0];
        if(m==2)return high;
        int i=0;
        int low=1;
        while(low<=high)
        {
            int mid=(low+high)/2;
            if(isPossible(position,m,mid))low=mid+1;
            else high=mid-1;
        }return high;
    }
}
