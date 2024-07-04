# July-4
## 2181. Merge Nodes in Between Zeros
```java
class Solution {
    public ListNode mergeNodes(ListNode head) {
        ListNode temp=head.next,zeroNode=head;
        int sum=0;
        while(temp.next!=null)
        {
            if(temp.val!=0)sum+=temp.val;
            else
            {
                zeroNode.val=sum;
                sum=0;
                zeroNode.next=temp;
                zeroNode=zeroNode.next;
            }temp=temp.next;
        }zeroNode.val=sum;
        zeroNode.next=null;
        return head; 
    }
}
