# February-28
## 513. Find the Bottom Left Tree Value
```java
class Solution {
    public int findBottomLeftValue(TreeNode root) {
        Queue<TreeNode> q = new LinkedList<>();
        q.offer(root);
        int level = 0, currLevel = 0,val = root.val;;
        while (!q.isEmpty()) {
            int size=q.size();
            for (int i = 1; i <= size; i++) {
                TreeNode node = q.poll();
                if (currLevel < level) {
                    level = currLevel;
                    val = node.val;
                }
                if(node.left!=null)q.offer(node.left);
                if(node.right!=null)q.offer(node.right);
            }
            currLevel--;
        }return val;
    }
}
