# July-18
## 1530. Number of Good Leaf Nodes Pairs
```java
class Solution {
    public int countPairs(TreeNode root, int distance) {
        List<TreeNode> leafNodes = new ArrayList<>();
        findLeafNodes(root, leafNodes);

        Map<TreeNode, List<TreeNode[]>> lcaMap = new HashMap<>();
        for (int i = 0; i < leafNodes.size(); i++) {
            for (int j = i + 1; j < leafNodes.size(); j++) {
                TreeNode lca = findLCA(root, leafNodes.get(i), leafNodes.get(j));
                lcaMap.computeIfAbsent(lca, k -> new ArrayList<>())
                      .add(new TreeNode[]{leafNodes.get(i), leafNodes.get(j)});
            }
        }

        int count = 0;
        for (Map.Entry<TreeNode, List<TreeNode[]>> entry : lcaMap.entrySet()) {
            for (TreeNode[] pair : entry.getValue()) {
                int dist = distance(entry.getKey(), pair[0]) + distance(entry.getKey(), pair[1]);
                if (dist <= distance) {
                    count++;
                }
            }
        }
        return count;
    }

    private void findLeafNodes(TreeNode node, List<TreeNode> leafNodes) {
        if (node == null) return;
        if (node.left == null && node.right == null) {
            leafNodes.add(node);
            return;
        }
        findLeafNodes(node.left, leafNodes);
        findLeafNodes(node.right, leafNodes);
    }

    private TreeNode findLCA(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null || root == p || root == q) return root;
        TreeNode left = findLCA(root.left, p, q);
        TreeNode right = findLCA(root.right, p, q);
        if (left != null && right != null) return root;
        return left != null ? left : right;
    }

    private int distance(TreeNode root, TreeNode target) {
        if (root == null) return -1;
        if (root == target) return 0;
        int leftDist = distance(root.left, target);
        if (leftDist >= 0) return leftDist + 1;
        int rightDist = distance(root.right, target);
        if (rightDist >= 0) return rightDist + 1;
        return -1;
    }
}
