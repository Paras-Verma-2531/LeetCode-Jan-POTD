# August-13
## 40. Combination Sum II
```java
class Solution {
    private void combinationSum(int[]arr,int target,int ind,
    ArrayList<Integer>temp,List<List<Integer>>ans)
    {
        if(target==0){ans.add(new ArrayList<Integer>(temp));return;}
        for(int i=ind;i<arr.length;i++)
        {
            if(i>ind&&arr[i]==arr[i-1])continue;
            if(arr[i]<=target)
            {
                temp.add(arr[i]);
                combinationSum(arr,target-arr[i],i+1,temp,ans);
                temp.remove(temp.size()-1);
            }
        }
    }
    public List<List<Integer>> combinationSum2(int[] arr, int target) {
        Arrays.sort(arr);
        List<List<Integer>>ans=new ArrayList<>();
        combinationSum(arr,target,0,new ArrayList<Integer>(),ans);
        return ans;
    }
}
