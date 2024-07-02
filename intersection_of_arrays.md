# July-2
## 350. Intersection of Two Arrays II
```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        List<Integer>ans=new ArrayList<>();
        int i=0,j=0;
        while(i<nums1.length && j<nums2.length)
        {
            if(nums1[i]==nums2[j])
            {
                ans.add(nums1[i]);
                i++;
                j++;
            }
            else if(nums1[i]<nums2[j])i++;
            else j++;
        }
        i=0;
        int[]arr=new int[ans.size()];
        for(int ele:ans)arr[i++]=ele;
        return arr;
    }
}
