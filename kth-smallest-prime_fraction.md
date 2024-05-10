# May-10
## 786. k-th Smallest Prim Fraction
```java
class Solution {
    public int[] kthSmallestPrimeFraction(int[] arr, int k) {
        Map<Double,int[]>map=new HashMap<>();
        PriorityQueue<Double>pq=new PriorityQueue<>(Collections.reverseOrder());
        for(int i=0;i<arr.length;i++)
        {
            for(int j=i+1;j<arr.length;j++)
            {
                double frac=(double)arr[i]/arr[j];
                map.put(frac,new int[]{arr[i],arr[j]});
                pq.offer(frac);
                if(pq.size()>k)pq.poll();
            }
        }
        return map.get(pq.poll());
    }
}
