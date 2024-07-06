# July-6
## 2582. Pass the Pillow
```java
class Solution {
    public int passThePillow(int n, int time) {
        int count=1;
        boolean directionReverse=false;
        while(time--!=0)
        {
            if(!directionReverse)
            {
               count++;
               if(count==n)directionReverse=true;
            }
            else
            {
                count--;
                if(count==1)directionReverse=false;
            }
        }return count;
    }
}
