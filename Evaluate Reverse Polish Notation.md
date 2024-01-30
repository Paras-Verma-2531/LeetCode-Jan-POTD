# January-30 

## 150. Evaluate Reverse Polish Notation

```java
class Solution {
  public int evalRPN(String[] tokens) {
    var stack = new Stack<Integer>();

    for (String token : tokens) {
      if (token.equals("+") || token.equals("-") || token.equals("*") || token.equals("/")) {
        int b = stack.pop();
        int a = stack.pop();

        if (token.equals("+"))
          stack.push(a + b);
        else if (token.equals("-"))
          stack.push(a - b);
        else if (token.equals("*"))
          stack.push(a * b);
        else if (token.equals("/"))
          stack.push(a / b);
      } else
        stack.push(Integer.parseInt(token));
    }
    return stack.pop();
  }
}
