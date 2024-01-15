# January-15

## 2225. Find Players with Zero or One Losses.

```java
class Solution {
    public List<List<Integer>> findWinners(int[][] matches) {
        Set<Integer>set=new HashSet<>();
        Map<Integer,Integer>loosers=new TreeMap<>();
        for(int i=0;i<matches.length;i++)
        {
            set.add(matches[i][0]);
            loosers.put(matches[i][1],loosers.getOrDefault(matches[i][1],0)+1);
        }
        List<Integer>winners=new ArrayList<>(set);
        Collections.sort(winners);
        List<List<Integer>>ans=new ArrayList<>();
        List<Integer>win=new ArrayList<>();
        List<Integer>lost=new ArrayList<>();
        for(int i:winners)
        {
           if(!loosers.containsKey(i))win.add(i);
        }
        for(int key:loosers.keySet())
        {
            if(loosers.get(key)==1)lost.add(key);
        }
        ans.add(new ArrayList<>(win));
        ans.add(new ArrayList<>(lost));
        return ans;
    }
}
