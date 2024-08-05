# August-5
## 2053. Kth Distinct String in an Array
```java
class Solution {
    public String kthDistinct(String[] arr, int k) {
        Map<String,Integer>map=new LinkedHashMap<>();
        for(String str:arr)map.put(str,map.getOrDefault(str,0)+1);
        String ans="";
        for(String keys:map.keySet())
        {
            if(map.get(keys)==1)
            {
                k--;
                if(k==0)
                {
                    ans=keys;
                    break;
                }
            }
        }return ans;
    }
}
