# February-27
## 543. Diameter of Binary Tree
```java

class Solution {
    private int height(TreeNode root,int[]ans)
    {
        if(root==null)return 0;
        int leftHeight=height(root.left,ans);
        int rightHeight=height(root.right,ans);
        ans[0]=Math.max(ans[0],leftHeight+rightHeight);
        return 1+ Math.max(leftHeight,rightHeight);
    }
    public int diameterOfBinaryTree(TreeNode root) {
        int[]ans={0};
        height(root,ans);
        return ans[0];
    }
}
