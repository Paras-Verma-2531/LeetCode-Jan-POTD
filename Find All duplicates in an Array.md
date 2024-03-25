# March-25
## 442. Find All duplicates in an Array
```java
class Solution {
    public void swap(int[] arr,int i,int j)
    {
        int temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
    }
    public void cyclicSort(int[]arr,int size)
    { int i=0;
        ArrayList<Integer> list=new ArrayList<>();
        while(i<size)
        {
                int correct=arr[i]-1;
                if(arr[correct]!=arr[i])swap(arr,i,correct);
            else i++;
        }
    }
    public List<Integer> findDuplicates(int[] nums) {
        ArrayList<Integer>list=new ArrayList<>();
        cyclicSort(nums,nums.length);
        for(int i=0;i<nums.length;i++)
          if(nums[i]!=i+1)list.add(nums[i]);
        return list;
        
    }
}
