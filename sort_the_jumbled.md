# July-24
## 2191. Sort the Jumbled Numbers
```java
class Solution {
    private int getValue(int num,int[]mapping)
    {
        int ans=0;
        for(char ch:Integer.toString(num).toCharArray())
        {
            ans=ans*10 + mapping[ch-'0'];
        }return ans;
    }
    public int[] sortJumbled(int[] mapping, int[] nums) {
        PriorityQueue<Pair>pq=new  PriorityQueue<>(new Comparator<Pair>()
        {
            public int compare(Pair a,Pair b)
            {
                if(a.val==b.val)return a.ind-b.ind;
                return a.val-b.val;
            }
        });
        int[]ans=new int[nums.length];
        for(int i=0;i<nums.length;i++)
        {
            int val=getValue(nums[i],mapping);
            pq.offer(new Pair(i,val));
        }
        int i=0;
        while(!pq.isEmpty())
        {
            ans[i++]=nums[pq.poll().ind];
        }
        return ans;
    }
    class Pair
    {
        int ind,val;
        public Pair(int ind,int val)
        {
            this.ind=ind;
            this.val=val;
        }
    }
}
