# March-13
## 2485. Find the Pivot Integer
```java
class Solution {
    public int pivotInteger(int n) {
        int sum=0;
        sum=(n*(n+1))/2;
        int low=1,high=n;
        while(low<=high)
        {
            int mid=(low+high)/2;
            int sumOfLeft=(mid*(mid+1))/2;
            int remSum=sum-sumOfLeft+mid;
            if(sumOfLeft==remSum)return mid;
            if(sumOfLeft<remSum)low++;
            else high--;
        }return -1;
    }
}
