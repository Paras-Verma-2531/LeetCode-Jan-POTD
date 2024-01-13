# January-12 

## 1704. Determine if String Halves Are Alike

```java
class Solution {
    public boolean halvesAreAlike(String s) {
        int i=0,n=s.length();
        Character[]ch={'a','e','i','o','u','A','E','I','O','U'};
        List<Character>vowels=Arrays.asList(ch);
        int count1=0,count2=0;
        for(i=0;i<n/2;i++)
        {
            if(vowels.contains(s.charAt(i)))count1++;
            if(vowels.contains(s.charAt(i+n/2)))count2++;
        }return count1==count2;
    }
}
