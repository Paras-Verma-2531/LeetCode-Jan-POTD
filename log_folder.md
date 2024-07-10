# July-10
## 1598. Crawler Log Folder
```java
class Solution {
    public int minOperations(String[] logs) {
        //at the beginning, we are at root level
        int level=0;
        for(String str:logs)
        {
            if(str.equals("./"))continue;//remain in the same level
            else if(str.equals("../"))
            {
                if(level==0)continue;// if already in the root, remain there
                level--;//else move to parent
            }else level++;//go to the next level
        }return level;
    }
}
