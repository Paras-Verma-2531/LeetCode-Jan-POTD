# February-22
## 997. Find the Town Judge
```java
class Solution { 
    public int findJudge(int n, int[][] trust) {
        int[]arr=new int[n+1];
        int[]occ=new int[n+1];
        if(trust.length==n)return -1;
        for(int i=0;i<trust.length;i++)
        {
            arr[trust[i][1]]++;
            occ[trust[i][0]]++;
        }
        for(int i=1;i<=n;i++)
        {
            if(arr[i]==n-1&&occ[i]==0)return i;
        }
        return -1;
    }
}
