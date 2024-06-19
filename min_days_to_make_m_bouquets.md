# June-19
## 1482. Min Days to make m Bouquets
```java
class Solution {
    private boolean isPossible(int[]arr,int m,int k,int currDay)
    {
        int bouq=0,count=0;
        for(int bloomday:arr)
        {
            if(bloomday<=currDay)count++;
            else
            {
                bouq+=count/k;
                count=0;
            }
        }
        bouq+=count/k;
        return bouq>=m;
    }
    public int minDays(int[] bloomDay, int m, int k) {
        if(bloomDay.length<(long)m*k)return -1;
        int min=Integer.MAX_VALUE,max=Integer.MIN_VALUE;
        for(int i:bloomDay)
        {
            min=Math.min(min,i);
            max=Math.max(i,max);
        }
        while(min<=max)
        {
            int mid=min+(max-min)/2;
            System.out.println(mid);
            if(isPossible(bloomDay,m,k,mid))max=mid-1;
            else min=mid+1;
        }return min;
    }
}
