# August-4
## 1508. Range Sum of Sorted Subarrays Sum
```java
class Solution {
    public int rangeSum(int[] nums, int n, int left, int right) {
        ArrayList<Integer>arr=new ArrayList<>();
        for(int i=0;i<n;i++)
        {
            int sum=0;
            for(int j=i;j<n;j++)
            {
                sum+=nums[j];
                arr.add(sum);
            }
        }
        Collections.sort(arr);
        int rangeSum=0;
        for(int i=left-1;i<right;i++)
        {
            rangeSum+=arr.get(i);
            rangeSum%=1000000007;
        }return rangeSum;
    }
}
