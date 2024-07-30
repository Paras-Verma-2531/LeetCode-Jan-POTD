# July-30
##1653. Minimum Deletions to Make String balanced
```java
class Solution {
    public int minimumDeletions(String s) {
        int countB = 0; 
        int deletions = 0;
        for (char ch : s.toCharArray()) {
            if (ch == 'b') {
                countB++; 
            } else {
                if (countB > 0) {
                    deletions++;
                    countB--; 
                }
            }
        }

        return deletions;
    }
