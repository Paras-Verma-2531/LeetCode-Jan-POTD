# March-6
## 141. LinkedList Cycle
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head==null||head.next==null)return false;
        ListNode fast=head,slow=head;
        while(fast!=null&&fast.next!=null)
        {
            fast=fast.next.next;
            slow=slow.next;
            if(slow==fast)return true;
        }return false;
    }
}
