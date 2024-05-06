# May-6
## 2487. Remove Nodes From LinkedList
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
    public ListNode removeNodes(ListNode head) {
        Stack<Integer>stack= new Stack<>();
        if(head.next==null)return head;
        ListNode revHead=reverse(head);
        ListNode temp=revHead;
        ListNode newHead=new ListNode(10001);
        ListNode dummy=newHead;
        ListNode nextNode=null;
        while(temp!=null)
        {
            while(!stack.isEmpty()&&stack.peek()<=temp.val)stack.pop();
            temp.val=stack.isEmpty()?temp.val:-1;
            nextNode=temp.next;
            if(temp.val!=-1)
            {
                temp.next=dummy.next;
                dummy.next=temp;
                stack.push(temp.val);
            }
            temp=nextNode;
        }
        return dummy.next;
    }
}
