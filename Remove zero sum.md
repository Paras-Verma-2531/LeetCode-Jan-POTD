# March-12
## 1171. Remove Zero Sum Consecutives
```java
class Solution {
    public ListNode removeZeroSumSublists(ListNode head) {
        Map<Integer,ListNode>map=new HashMap<>();
        int sum=0;
        ListNode dummy=new ListNode(0);
        dummy.next=head;
        ListNode temp=dummy;
        while(temp!=null)
        {
            sum+=temp.val;
            map.put(sum,temp);
            temp=temp.next;
        }sum=0;
        temp=dummy;
        while(temp!=null)
        {
            sum+=temp.val;
            if(map.containsKey(sum))
            {
                ListNode node=map.get(sum);
                if(temp!=node)
                    temp.next=node.next;
            }temp=temp.next;
        }return dummy.next;
            
    }
}
