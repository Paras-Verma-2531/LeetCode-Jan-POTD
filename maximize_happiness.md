# May-9
## 3075. Maximize Happiness of Selected Children
```java
class Solution {
    public long maximumHappinessSum(int[] happiness, int k) {
        PriorityQueue<Integer>pq=new PriorityQueue<>(k,Collections.reverseOrder());
        for(int ele:happiness)pq.offer(ele);
        long maxHappiness=0;
        maxHappiness+=pq.poll();
        int val=1;
        k--;
        while(k>0)
        {
            int happ=pq.poll();
           maxHappiness+=happ-val>0?happ-val:0;
           val++;
           k--;
        }return maxHappiness;
    }
}
