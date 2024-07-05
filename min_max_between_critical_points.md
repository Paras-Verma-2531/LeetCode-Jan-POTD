# July-5
## 2058. Find the Minimum and Maximum Number of Nodes Between Critical Points
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
    private int getLength(ListNode head)
    {
        ListNode temp=head;
        int length=0;
        while(temp!=null)
        {
            ++length;
            temp=temp.next;
        }return length;
    }
    public int[] nodesBetweenCriticalPoints(ListNode head) {
        int len=getLength(head);
        int[]listArr=new int[len];
        int i=0;
        int[]arr={-1,-1};
        if(len-2<2)return arr;
        ListNode temp=head;
        while(temp!=null)
        {
            listArr[i++]=temp.val;
            temp=temp.next;
        }
        List<Integer>criticalPoints=new ArrayList<>();
        for(i=1;i<listArr.length-1;i++)
        {
            if(
                listArr[i]<listArr[i-1]
                && listArr[i]<listArr[i+1]
                || listArr[i]>listArr[i-1]
                && listArr[i]>listArr[i+1]
            )criticalPoints.add(i+1);
        }
        int size=criticalPoints.size();
        if(size<2)return arr;
        int minDis=Integer.MAX_VALUE,maxDis=Integer.MIN_VALUE;
        for(i=0;i<size-1;i++)
        {
            minDis=Math.min(minDis,Math.abs(criticalPoints.get(i)-criticalPoints.get(i+1)));
        }
        maxDis=Math.abs(criticalPoints.get(0)-criticalPoints.get(size-1));
        arr[0]=minDis;arr[1]=maxDis;
        return arr;
    }
}
