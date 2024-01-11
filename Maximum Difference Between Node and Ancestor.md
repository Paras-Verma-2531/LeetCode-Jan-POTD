# January-11 

## 1026. Maximum Difference Between Node and Ancestor

```java
private int maxDiff(TreeNode root,int max,int min)
    {
        if(root==null)return Math.abs(max-min);
        max=Math.max(max,root.val);
        min=Math.min(min,root.val);
        int left=maxDiff(root.left,max,min);
        int right=maxDiff(root.right,max,min);
        return Math.max(left,right);
    }
    public int maxAncestorDiff(TreeNode root) {
       if(root==null)return 0;
       return maxDiff(root,root.val,root.val);
    }
