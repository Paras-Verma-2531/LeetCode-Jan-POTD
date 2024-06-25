# June-25
## 1038. Binary Search Tree to Greater Tree
```java
class Solution {
    private void bstToGst(TreeNode root,int[]sum)
    {
        if(root==null)return;
        bstToGst(root.right,sum);
        root.val+=sum[0];
        sum[0]=root.val;
        bstToGst(root.left,sum);
    }
    public TreeNode bstToGst(TreeNode root) {
        int[]sum={0};
        bstToGst(root,sum);
        return root;
    }
}
