# May-21
## 78. Subsets
```java
class Solution {
    private void subsets(int[]arr,int ind,List<List<Integer>>ans,ArrayList<Integer>temp)
    {
        if(ind==arr.length)
        {
            ans.add(new ArrayList<Integer>(temp));
            return;
        }
        temp.add(arr[ind]);
        subsets(arr,ind+1,ans,temp);
        temp.remove(temp.size()-1);
        subsets(arr,ind+1,ans,temp);
    }
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>>finalAns=new ArrayList<>();
        subsets(nums,0,finalAns,new ArrayList<Integer>());
        return finalAns;
    }
}
