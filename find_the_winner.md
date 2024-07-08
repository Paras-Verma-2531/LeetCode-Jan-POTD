# July-8
## 1823. Find the Winner of the Circular Game
```java
class Solution {
    public int findTheWinner(int n, int k) {
        Queue<Integer>q=new LinkedList<>();
        for(int i=1;i<=n;i++)
        {
            q.offer(i);
        }
        //repeat till the size of q > 1
        int count=1;
        while(q.size()!=1)
        {
            int person=q.poll();
            if(count==k)
            {
                count=1;
            }
            else
            {
                count++;
                q.offer(person);
            }
        }return q.peek();
    }
}
