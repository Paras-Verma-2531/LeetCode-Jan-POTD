# June-27
## 1791. Find Center of Star Graph
```java
class Solution {
    public int findCenter(int[][] edges) {
        ArrayList<ArrayList<Integer>>list=new ArrayList<>();
        int n=edges.length;
        for(int i=0;i<=n+1;i++)
        {
            list.add(new ArrayList<Integer>());
        }
        for(int i=0;i<n;i++)
        {
            int u=edges[i][0];
            int v=edges[i][1];
            list.get(u).add(v);
            list.get(v).add(u);
        }
        for(int i=1;i<list.size();i++)
        {
            if(list.get(i).size()==edges.length)return i;
        }return 1;
    }
}
