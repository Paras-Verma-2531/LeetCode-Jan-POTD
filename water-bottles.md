# July-7
## 1518. Water Bottles
```java
class Solution {
    public int numWaterBottles(int numBottles, int numExchange) {
        int totalCount=numBottles;
        int extraGot=0;
        while(numBottles>=numExchange)
        {
            extraGot=numBottles/numExchange;
            totalCount+=extraGot;
            numBottles=extraGot+ numBottles%numExchange;
        }
        
        return totalCount;
    }
}
