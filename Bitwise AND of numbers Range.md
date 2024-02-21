# Febuary-21
## 201. Bitwise AND of numbers Range
```java
//brute -TLE
/*
class Solution {
    public int rangeBitwiseAnd(int left, int right) {
       if(left==0)return 0;
       if(left==right)return left;
       long end=right;
       long ans=left;
       for(long i=left+1;i<=end;i++)
       {
           ans=ans&i;
           if(ans==0)return 0;
       } return (int)ans;
    }
}
*/
//OPTIMAL
class Solution {
    public int rangeBitwiseAnd(int left, int right) {
        int res = right;
        while(right > left) {
            res = right & (right-1);
            right = res;
        }
        return res;
        
    }
}
