# April-14
## 404. Sum of Left Leaves Node
```java
class Solution {
    private boolean isLeaf(TreeNode root)
    {
        return root.left==root.right;
    }
    private void sumOfLeftLeaves(TreeNode root,int[]sum,boolean flag)
    {
        if(root==null)return;
        if(isLeaf(root) && flag)sum[0]+=root.val;
        sumOfLeftLeaves(root.left,sum,true);
        sumOfLeftLeaves(root.right,sum,false);
    }
    public int sumOfLeftLeaves(TreeNode root) {
        if(isLeaf(root))return 0;
        int[]sum={0};
        sumOfLeftLeaves(root,sum,true);
        return sum[0];
    }
}
