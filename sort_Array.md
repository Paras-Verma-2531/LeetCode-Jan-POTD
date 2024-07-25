# July-25
## 912. Sort An Array
```java
class Solution {
    private void merge(int low,int mid,int high,int[]arr)
    {
        int[]temp=new int[high-low+1];
        int i=low,j=mid+1,k=0;
        while(i<=mid&&j<=high)
        {
           if(arr[i]<arr[j])temp[k++]=arr[i++];
           else temp[k++]=arr[j++];
        }
        while(i<=mid)temp[k++]=arr[i++];
        while(j<=high)temp[k++]=arr[j++];
        for(i=low;i<=high;i++)arr[i]=temp[i-low];
    }
    private void mergeSort(int low,int high,int[]arr)
    {
        if(low<high)
        {
            int mid=(low+high)/2;
            mergeSort(low,mid,arr);
            mergeSort(mid+1,high,arr);
            merge(low,mid,high,arr);
        }
    }
    public int[] sortArray(int[] nums) {
        mergeSort(0,nums.length-1,nums);
        return nums;
    }
}
