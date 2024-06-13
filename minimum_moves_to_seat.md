# June-13
## 2037. Minimum Number of Moves to Seat Everyone
```java
class Solution {
    public int minMovesToSeat(int[] seats, int[] students) {
     Arrays.sort(seats);
     Arrays.sort(students);
     int i=0,n=seats.length;
     int totalMoves=0;
     while(i<n)
     {
        totalMoves+=Math.abs(seats[i]-students[i]);
        i++;
     }return totalMoves;
    }
}
