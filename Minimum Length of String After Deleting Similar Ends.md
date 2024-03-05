# March-5
## 1750. Minimum Length of String After Deleting Similar Ends
```java
class Solution {
    public int minimumLength(String s) {
        if (s.length() == 0 || s.charAt(0) != s.charAt(s.length() - 1))
            return s.length();
       int left = 0, right = s.length() - 1;
        while (left < right && s.charAt(left) == s.charAt(right)) {
            char currentChar = s.charAt(left);
            while (left <= right && s.charAt(left) == currentChar)left++;
            while (left <= right && s.charAt(right) == currentChar)right--;
        }
        return right - left + 1;
    }
}
