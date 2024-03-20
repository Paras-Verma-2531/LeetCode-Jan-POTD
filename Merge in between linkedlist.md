# March-20
## 1669. Merge In Between LinkedList
```java
class Solution {
    public ListNode mergeInBetween(ListNode list1, int a, int b, ListNode list2) {
        ListNode dummy=new ListNode(-100,list1);
        ListNode temp=list1;
        while(--a>0)temp=temp.next;
        ListNode temp2=list1;
        while(b-->=0)temp2=temp2.next;
        if(temp2!=null)System.out.println("temp 2 data is "+temp2.val);
        temp.next=list2;
        temp=list2;
        while(temp.next!=null)temp=temp.next;
        temp.next=temp2;
        return list1;
    }
}
