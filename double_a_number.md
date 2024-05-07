# May-7
## 2816. Double a Number Represented as LinkedList
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    private ListNode reverse(ListNode head)
    {
        ListNode curr=head,prev=null,nextnode=null;
        while(curr!=null)
        {
            nextnode=curr.next;
            curr.next=prev;
            prev=curr;
            curr=nextnode;
        }return prev;
    }
    public ListNode doubleIt(ListNode head) {
        ListNode newHead=reverse(head);
        ListNode temp=newHead;
        int sum=0,carry=0;
        ListNode prev=null;
        while(temp!=null)
        {
            sum=carry+2*temp.val;
            temp.val=sum%10;
            carry=sum/10;
            prev=temp;
            temp=temp.next;
        }
        if(carry>0)prev.next=new ListNode(carry);
        head=reverse(newHead);
        return head;
    }
}
