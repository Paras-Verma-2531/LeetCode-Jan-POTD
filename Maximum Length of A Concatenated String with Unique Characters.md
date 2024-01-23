# January-23 

## 1239. Maximum Length of A Concatenated String with Unique Characters

```java
class Solution {
    private void helper(List<String> arr,String str,int start,int[]maxLength)
    {
        if(maxLength[0]<str.length())maxLength[0]=str.length();
        for(int i=start;i<arr.size();i++)
        {
            if(!isValid(str,arr.get(i)))continue;
            helper(arr,str+arr.get(i),i+1,maxLength);
        }
    }
    private boolean isValid(String st1,String st2)
    {
        Set<Character>set=new HashSet<>();
        for(char ch:st1.toCharArray())set.add(ch);
        for(char ch:st2.toCharArray())set.add(ch);
        return set.size()==st1.length()+st2.length();
    }
    public int maxLength(List<String> arr) {
        int[]maxLength={0};
        helper(arr,"",0,maxLength);
        return maxLength[0];
    }
}
