# March-1
## 2864. Maximum Odd Binary Number
```java
class Solution {
    private void swap(char[]chr,int i,int j)
    {
        char ch=chr[i];
        chr[i]=chr[j];
        chr[j]=ch;
    }
    public String maximumOddBinaryNumber(String s) {
        char[]chr=s.toCharArray();
        int ind=-1;
        for(int i=0;i<chr.length;i++)
        {
            if(chr[i]=='1')
            {
                swap(chr,i,chr.length-1);
                ind=i;
                break;
            }
        }int j=0;
        while(ind<chr.length-1)
        {
            if(chr[ind]=='1')swap(chr,ind,j++);
            ind++;
        }return String.valueOf(chr);
    }
}
