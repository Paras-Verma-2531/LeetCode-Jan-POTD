# May-3
## 165. Compare Version Numbers
```java
class Solution {
    private int compareVersions(String[] arr1, String[] arr2, int length) {
        int i = 0;
        while (i < length) {
            int val1 = Integer.parseInt(arr1[i]);
            int val2 = Integer.parseInt(arr2[i]);
            if (val1 < val2)
                return -1;
            if (val1 > val2)
                return 1;
            i++;
        }
        if (arr1.length > arr2.length) {
            while (i < arr1.length) {
                int val = Integer.parseInt(arr1[i++]);
                if(val>0)return 1;
            }
        } else if (arr2.length > arr1.length) {
            while (i < arr2.length) {
                int val = Integer.parseInt(arr2[i++]);
                if(val>0)return -1;
            }
        }
        return 0;
    }

    public int compareVersion(String ver1, String ver2) {
        String[] version1 = ver1.split("\\.");
        String[] version2 = ver2.split("\\.");
        // System.out.println(Arrays.toString(version1));
        // System.out.println(Arrays.toString(version2));
        int n = version1.length;
        int m = version2.length;
        return compareVersions(version1, version2, n < m ? n : m);
    }
}
