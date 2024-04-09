# April-9
## 2073. Time Needed to Buy Tickets
```java
class Solution {
    public int timeRequiredToBuy(int[] tickets, int k) {
        Queue<Integer>q=new LinkedList<>();
        for(int ticket:tickets)q.offer(ticket);
        int time=0,ind=0;
        while(!q.isEmpty()&&tickets[k]!=0)
        {
            if(ind==tickets.length)ind=0;
            if(q.peek()>0)
            {
                time++;
                tickets[ind]=tickets[ind]-1;
                q.offer(q.poll()-1);
            }else q.offer(q.poll());
            ind++;
        }return time;
    }
}
