# June-2
## 344. Reverse a String
```java
class Solution {
    private void swap(char[]arr,int i,int j)
    {
        char temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
    }
    public void reverseString(char[] s) {
        int i=0,j=s.length-1;
        while(i<=j)
        {
            swap(s,i,j);
            i++;
            j--;
        }
    }
}
