# Aug-1
## 2678. Number of Senior Citizens
```java
class Solution {
    public int countSeniors(String[] details) {
        int seniorCitizens=0;
        for(String detail:details)
        {
            if(Integer.parseInt(detail.substring(11,13))>60)seniorCitizens++;
        }return seniorCitizens;
    }
}
