# Febuary-19 

## 231. Power of Two

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        return n>0&&(n&n-1)==0;
    }
}
