# August-25
## 145. PostOrder traversal
```java
class Solution {
    private void postOrder(TreeNode root,List<Integer>post)
    {
        if(root==null)return;
        postOrder(root.left,post);
        postOrder(root.right,post);
        post.add(root.val);
    }
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer>post=new ArrayList<>();
        postOrder(root,post);
        return post;
    }
}
