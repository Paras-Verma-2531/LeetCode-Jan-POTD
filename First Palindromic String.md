# Febuary-13

## 2108. First Palindromic String

```java
class Solution {
    private boolean checkIfPalindrome(String st)
    {
        int i=0,j=st.length()-1;
        while(i<=j)
        {
            if(st.charAt(i)!=st.charAt(j))return false;
            i++;
            j--;
        }return true;
    }
    public String firstPalindrome(String[] words) {
        for(String str:words)
        {
            if(checkIfPalindrome(str))return str;
        }return "";
    }
}
