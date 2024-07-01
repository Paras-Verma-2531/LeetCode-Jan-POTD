# July-1
## 1550. Three Consecutive Odds
```java
class Solution {
    public boolean threeConsecutiveOdds(int[] arr) {
        int n=arr.length;
        if(n<3)return false;
        //check for the first ele as odd
        if(arr[0]%2!=0 && arr[1]%2!=0 && arr[2]%2!=0
        ||arr[n-1]%2!=0 && arr[n-2]%2!=0 && arr[n-3]%2!=0)return true;
        for(int i=1;i<n-1;i++)
        {
            if(arr[i]%2!=0 && arr[i-1]%2!=0 && arr[i+1]%2!=0)return true;
        }return false;
    }
}
