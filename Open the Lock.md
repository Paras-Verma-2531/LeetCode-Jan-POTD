# April-22
## 752. Open the Lock
```java
class Solution {
    private char turnLeft(char ch) {
        return ch == '0' ? '9' :(char)( ch - 1);
    }
    private char turnRight(char ch) {
        return ch == '9' ? '0' : (char)(ch + 1);
    }
    private List<String> nextOptions(String st) {
        List<String> ans = new ArrayList<>();
        for (int i = 0; i < st.length(); i++) {
            StringBuilder copy = new StringBuilder(st);
            char ch = st.charAt(i);
            copy.setCharAt(i, turnLeft(ch));
            ans.add(copy.toString());
            copy.setCharAt(i, turnRight(ch));
            ans.add(copy.toString());
        }
        return ans;
    }
    public int openLock(String[] deadends, String target) {
        Set<String> deadSet = new HashSet<>(Arrays.asList(deadends));
        Set<String> visited = new HashSet<>();
        Queue<String> q = new LinkedList<>();
        q.offer("0000");
        visited.add("0000");
        int level = 0;
        while (!q.isEmpty()) {
            int size = q.size();
            while (size-- > 0) {
                String current = q.poll();
                if (deadSet.contains(current))
                    continue;
                if (current.equals(target))
                    return level;
                for (String next : nextOptions(current)) {
                    if (!visited.contains(next) && !deadSet.contains(next)) {
                        visited.add(next);
                        q.offer(next);
                    }
                }
            }
            level++;
        }
        return -1;
    }
}
