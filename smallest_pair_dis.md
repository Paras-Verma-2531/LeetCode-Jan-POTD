# August-14
## 719. Find k-th Smallest Pair Distance
```java
class Solution {
    public int smallestDistancePair(int[] nums, int k) {
        PriorityQueue<Integer>pq=new PriorityQueue<>(Collections.reverseOrder());
        for(int i=0;i<nums.length;i++)
        {
            for(int j=i+1;j<nums.length;j++)
            {
                pq.offer(Math.abs(nums[i]-nums[j]));
                if(pq.size()>k)pq.poll();
            }
        }return pq.peek();
    }
}
