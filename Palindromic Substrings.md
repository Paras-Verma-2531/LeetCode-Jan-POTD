# Febuary-10

## 300. Palindromic Substrings

```java
class Solution {
    private boolean isPalindrome(char[]ch,int i,int j)
    {
        while(i<=j)
        {
            if(ch[i]!=ch[j])return false;
            i++;
            j--;
        }return  true;
    }
    public int countSubstrings(String s) {
        char[]ch=s.toCharArray();
        int count=0;
        for(int i=0;i<s.length();i++)
        {
            for(int j=i;j<s.length();j++)
            {
                if(isPalindrome(ch,i,j))count++;
            }
        }return count;
    }
}
