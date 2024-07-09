# July-9
## 1701. Average Waiting Time
```java
class Solution {
    public double averageWaitingTime(int[][] customers) {
        int compleTime=customers[0][0];
        double waitingTime=0.0;
        for(int[]customer:customers)
        {
            if(compleTime<customer[0])compleTime=customer[0];
            compleTime+=customer[1];
            waitingTime+=compleTime-customer[0];
        }return waitingTime/customers.length;
    }
}
