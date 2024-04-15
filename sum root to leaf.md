# April-15
## 129. Sum Root to Leaf Numbers
```java
class Solution {
    private boolean isLeaf(TreeNode root)
    {
        return root.left==root.right;
    }
    private void sumNumbers(TreeNode root,int sum,int[]finalAns)
    {
      if(root==null)return;
      if(isLeaf(root))
      {
        sum=sum*10 + root.val;
        finalAns[0]+=sum;
        return;
      }
      sumNumbers(root.left,sum*10+root.val,finalAns);
      sumNumbers(root.right,sum*10+root.val,finalAns);
    }
    public int sumNumbers(TreeNode root) {
        int[]finalAns={0};
        sumNumbers(root,0,finalAns);
        return finalAns[0];
    }
}
