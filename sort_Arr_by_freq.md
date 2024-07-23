# July-23
## 1613. Sort Array by Increasing Frequency
```java
import java.util.*;

class Solution {
    public int[] frequencySort(int[] nums) {
        Map<Integer, Integer> frequencyMap = new HashMap<>();

        for (int num : nums) {
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
        }

        PriorityQueue<Pair> minHeap = new PriorityQueue<>(new Comparator<Pair>() {
            public int compare(Pair a, Pair b) {
                if (a.freq == b.freq) {
                    return Integer.compare(b.value, a.value);
                }
                return Integer.compare(a.freq, b.freq);
            }
        });
        for (Map.Entry<Integer, Integer> entry : frequencyMap.entrySet()) {
            int num = entry.getKey();
            int freq = entry.getValue();
            minHeap.offer(new Pair(num, freq));
        }

        int[] result = new int[nums.length];
        int index = 0;

        while (!minHeap.isEmpty()) {
            Pair pair = minHeap.poll();
            int num = pair.value;
            int freq = pair.freq;

            for (int i = 0; i < freq; i++) {
                result[index++] = num;
            }
        }

        return result;
    }

    class Pair {
        int value, freq;

        public Pair(int value, int freq) {
            this.value = value;
            this.freq = freq;
        }
    }
}
