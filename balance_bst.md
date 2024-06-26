# June-26
## 1382. Balance a Binary Search Tree
```java
class Solution {
    private void getInorder(TreeNode root,List<Integer>inorder)
    {
        if(root==null)return;
        getInorder(root.left,inorder);
        inorder.add(root.val);
        getInorder(root.right,inorder);
    }
    private TreeNode buildTree( List<Integer>inorder,int start,int end)
    {
        if(start>end)return null;
        int mid=(start+end)/2;
        TreeNode root=new TreeNode(inorder.get(mid));
        root.left=buildTree(inorder,start,mid-1);
        root.right=buildTree(inorder,mid+1,end);
        return root;
    }
    public TreeNode balanceBST(TreeNode root) {
        List<Integer>inorder=new ArrayList<>();
        getInorder(root,inorder);
        root=buildTree(inorder,0,inorder.size()-1);
        return root;
    }
}
