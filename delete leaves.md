# May-17
## 1325. Delete Leaves With Given Value
```java
class Solution {
    private boolean isLeaf(TreeNode root)
    {
        return root.left==root.right;
    }
    private TreeNode deleteNode(TreeNode root,int tar)
    {
        if(root==null)return null;
        if(isLeaf(root))
        {
            return root.val==tar?null:root;
        }
        root.left=deleteNode(root.left,tar);
        root.right=deleteNode(root.right,tar);
        if(isLeaf(root))return deleteNode(root,tar);
        return root;
    }
    public TreeNode removeLeafNodes(TreeNode root, int target) {
        return deleteNode(root,target);
    }
}
