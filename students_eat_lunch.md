# April-8
## 1700. Number of Students Unable to Eat Lunch
```java
class Solution {
    public int countStudents(int[] students, int[] sandwiches) {
        Queue<Integer> stu = new LinkedList<>();
        Stack<Integer> sand = new Stack<>();
        int n = students.length;
        int count=0;
        for (int i = n - 1; i >= 0; i--) {
            sand.push(sandwiches[i]);
            stu.offer(students[n - i - 1]);
        }
        while (!sand.isEmpty() && !stu.isEmpty()) {
            if (sand.peek() == stu.peek()) {
                sand.pop();
                stu.poll();
                count = 0;
            } else {
                stu.offer(stu.poll());
                count++;
                if (count >= n)
                    break;
            }
        }
        return stu.size();
    }
}
