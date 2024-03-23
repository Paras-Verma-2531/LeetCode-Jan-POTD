# March-23
##  143. Reorder List
```java
class Solution {
    private ListNode getMiddle(ListNode head)
    {
        if(head==null||head.next==null)return head;
        ListNode fast=head.next,slow=head;
        while(fast!=null&&fast.next!=null)
        {
            fast=fast.next.next;
            slow=slow.next;
        }return slow;
    }
     private ListNode reverse(ListNode head)
    {
        if(head==null||head.next==null)return head;
        ListNode curr=head,nextnode=null,prev=null;
        while(curr!=null)
        {
           nextnode=curr.next;
           curr.next=prev;
           prev=curr;
           curr=nextnode;
        }return prev;
    }
    public void reorderList(ListNode head) {
        if(head.next==null)return;
        ListNode midprev=getMiddle(head);
        ListNode mid=midprev.next;
        midprev.next=null;
        ListNode reverseHead=reverse(mid);
        ListNode temp1=head,temp2=reverseHead,next1=null,next2=null;
        while(temp1!=null&&temp2!=null)
        {
            next1=temp1.next;
            next2=temp2.next;
            temp1.next=temp2;
            if(next1!=null)temp2.next=next1;
            temp1=next1;
            temp2=next2;
        }
    }
}
