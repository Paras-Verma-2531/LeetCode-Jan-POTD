# January-14

## 1657. Check if Two Strings Are Close

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public boolean closeStrings(String word1, String word2) {
        Map<Character, Integer> map1 = new HashMap<>();
        Map<Character, Integer> map2 = new HashMap<>();

        for (char ch : word1.toCharArray()) map1.put(ch, map1.getOrDefault(ch, 0) + 1);
        for (char ch : word2.toCharArray()) map2.put(ch, map2.getOrDefault(ch, 0) + 1);

        if (!map1.keySet().equals(map2.keySet())) {
            return false;
        }

        return frequencySetsEqual(map1, map2);
    }

    private boolean frequencySetsEqual(Map<Character, Integer> map1, Map<Character, Integer> map2) {
        Map<Integer, Integer> freqCount1 = new HashMap<>();
        Map<Integer, Integer> freqCount2 = new HashMap<>();

        for (int freq : map1.values()) freqCount1.put(freq, freqCount1.getOrDefault(freq, 0) + 1);
        for (int freq : map2.values()) freqCount2.put(freq, freqCount2.getOrDefault(freq, 0) + 1);

        return freqCount1.equals(freqCount2);
    }
}
