# July-29
## 621. Task Scheduler
```java
class Solution {
    public int leastInterval(char[] tasks, int n) {
        if(n==0)return tasks.length;
        int[]arr=new int[26];
        for(char task:tasks)arr[task-'A']++;
        PriorityQueue<Integer>pq=new PriorityQueue<>(Collections.reverseOrder());
        for(int val:arr)if(val>0)pq.offer(val);
        Queue<Pair<Integer,Integer>>q=new LinkedList<>();
        int time=0;
        while(!pq.isEmpty()||!q.isEmpty())
        {
            time++;
           if(!pq.isEmpty())
           {
            int val=pq.poll();
            val--;
            if(val>0)q.offer(new Pair(val,time+n));
           }
           if(!q.isEmpty()&&q.peek().getValue()==time)pq.offer(q.poll().getKey());
        }return time;

        
    }
}
