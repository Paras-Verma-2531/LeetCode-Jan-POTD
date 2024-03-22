# March-22
## 232 Palindrome LinkedList 
```java
class Solution {
    private ListNode reverse(ListNode head)
    {
        ListNode curr=head,nextnode=null,prev=null;
        while(curr!=null)
        {
            nextnode=curr.next;
            curr.next=prev;
            prev=curr;
            curr=nextnode;
        }return prev;
    }
    private ListNode findMiddle(ListNode head)
    {
        if(head.next==null)return head;
        ListNode fast=head,slow=head;
        while(fast!=null&&fast.next!=null)
        {
            fast=fast.next.next;
            slow=slow.next;
        }return slow;
    }
    public boolean isPalindrome(ListNode head) {
        if(head.next==null)return true;
        ListNode mid=findMiddle(head);
        ListNode dummy=reverse(mid);
        ListNode temp=head;
        while(dummy!=null)
        {
            if(temp.val!=dummy.val)return false;
            temp=temp.next;
            dummy=dummy.next;
        }return true;
    }
}
