# January-29 

## 232. Implement Queue using Stacks

```java
class MyQueue {

   Stack<Integer>q;
   Stack<Integer>s;
    public MyQueue() {
        s=new Stack<>();
        q=new Stack<>();
    }
    
    public void push(int x) {
        while(!q.isEmpty())s.push(q.pop());
        s.push(x);
        while(!s.isEmpty())q.push(s.pop());
    }
    
    public int pop() {
        return q.isEmpty()?-1:q.pop();
    }
    
    public int peek() {
        return q.isEmpty()?-1:q.peek();
    }
    
    public boolean empty() {
        return q.isEmpty();
    }
}
