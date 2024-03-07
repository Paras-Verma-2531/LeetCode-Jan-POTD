# March-7
## 876. Middle of the Linked List
```java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode fast=head,slow=head;
        while(fast!=null&&fast.next!=null)
        {
            fast=fast.next.next;
            slow=slow.next;
        }return slow;
    }
}
