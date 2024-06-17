# June-17
## 633. Sum of Square Numbers
```java
public boolean judgeSquareSum(int c) {
        long sum = c;
       long start = 0, end = (long) Math.sqrt(c)+1;
        while(start<=end)
        {
           long tempSum=(start*start)+(end*end);
           if(tempSum==sum)return true;
           if(tempSum<sum)start++;
           else end--;
        }return false;
    }
