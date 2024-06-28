# June-28
## 2285. Maximum Total Importance of Road
```java
class Solution {
    public long maximumImportance(int n, int[][] roads) {
        //count the importance:: by indegree
        long[]indegree=new long[n];
        for(int[]edge:roads)
        {
            indegree[edge[0]]++;
            indegree[edge[1]]++;
        }
        PriorityQueue<Pair>pq=new PriorityQueue<>(new Comparator<Pair>()
        {
            public int compare(Pair a, Pair b) {
                return Long.compare(a.degree, b.degree);
            }
        });
        for(int i=0;i<indegree.length;i++)
         pq.offer(new Pair(i,indegree[i]));
        long[]imp=new long[n];
        //set the initial importance  as 1
        long importance=1;
        while(!pq.isEmpty())
        {
            Pair p=pq.poll();
            int edge=p.edge;
            long degree=p.degree;
            imp[edge]=importance++;
        }
        long totalImp=0;
        for(int[]edge:roads)
        {
            totalImp+=imp[edge[0]]+imp[edge[1]];
        }return totalImp;
    }
    class Pair
    {
        int edge;long degree;
        public Pair(int edge,long degree)
        {
            this.edge=edge;
            this.degree=degree;
        }
    }
}
