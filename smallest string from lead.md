# April-17
##  988.Smallest String Starting From Leaf
```java
class Solution {
    private boolean isLeaf(TreeNode root)
    {
        return root.left==root.right;
    }
    private void smallestFromLeaf(TreeNode root,String st, String[]ans)
    {
        if(root==null)return;
        if(isLeaf(root))
        {
         st = (char) (root.val + 'a') + st;
         if(ans[0].length()==0||st.compareTo(ans[0])<0)ans[0]=st;
         return;
        }
        st = (char) (root.val + 'a') + st;
        smallestFromLeaf(root.left,st,ans);
        smallestFromLeaf(root.right,st,ans);
    }
    public String smallestFromLeaf(TreeNode root) {
        String ans[]={""};
        smallestFromLeaf(root,"",ans);
        return ans[0];
    }
}
