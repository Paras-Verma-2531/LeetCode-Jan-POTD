# Febuary-16

## 1481. Least Number of Unique Integers After K Removals

```java
class Solution {
    public int findLeastNumOfUniqueInts(int[] arr, int k) {
        Map<Integer,Integer>map=new HashMap<>();
        PriorityQueue<Pair>pq=new PriorityQueue<>(new Comparator<Pair>()
        {
            public int compare(Pair a,Pair b)
            {
                return a.freq-b.freq;
            }
        });
        for(int i:arr)map.put(i,map.getOrDefault(i,0)+1);
        for(int key:map.keySet())
        {
            pq.offer(new Pair(key,map.get(key)));
        }
        while(k!=0)
        {
           Pair p=pq.poll();
           if(p.freq>k)
           {
               pq.offer(new Pair(p.key,p.freq-k));
               break;
           }else
           {
               k=k-p.freq;
           }
        }return pq.size();
    }
    class Pair
    {
        int key,freq;
        public Pair(int key,int freq)
        {
            this.freq=freq;
            this.key=key;
        }
    }
}
