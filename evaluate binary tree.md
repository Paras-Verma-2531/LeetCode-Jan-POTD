# May-16
## 2331. Evaluate Boolean Binary Tree
```java
class Solution {
    private boolean isLeaf(TreeNode root)
    {
        return root.left==root.right;
    }
    public boolean evaluateTree(TreeNode root) {
        if(root==null)return true;
        if(isLeaf(root))return root.val==1;
        boolean left=evaluateTree(root.left);
        boolean right=evaluateTree(root.right);
        boolean ans=root.val==2?left||right:left&&right;
        return ans;
    }
}
