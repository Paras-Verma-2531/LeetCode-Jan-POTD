# March-21
##  206. Reverse LinkedList
```java
class Solution {
    public ListNode reverseList(ListNode head) {
        if(head==null||head.next==null)return head;
        ListNode newHead=reverseList(head.next);
        ListNode temp=head.next;
        temp.next=head;
        head.next=null;
        return newHead;
    }
}
