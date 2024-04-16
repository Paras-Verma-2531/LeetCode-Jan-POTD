# April-16
## 623. Add One Row to Tree
```java
class Solution {
    public TreeNode addOneRow(TreeNode root, int val, int depth) {
        if (depth == 1) {
            TreeNode newRoot = new TreeNode(val);
            newRoot.left = root;
            return newRoot;
        }
        addRow(root, val, depth, 1);
        return root;
    }
    
    private void addRow(TreeNode node, int val, int depth, int currDepth) {
        if (node == null) return;
        
        if (currDepth == depth - 1) {
            TreeNode leftNode = new TreeNode(val);
            leftNode.left = node.left;
            node.left = leftNode;
            
            TreeNode rightNode = new TreeNode(val);
            rightNode.right = node.right;
            node.right = rightNode;
        } else {
            addRow(node.left, val, depth, currDepth + 1);
            addRow(node.right, val, depth, currDepth + 1);
        }
    }
}
