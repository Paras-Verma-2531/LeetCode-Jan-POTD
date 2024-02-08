# Febuary-7

## 451. Sort Characters by Frequency

```java
class Solution {
    public String frequencySort(String s) {
        Map<Character,Integer>map=new HashMap<>();
        char[]chr=s.toCharArray();
        for(char ch:chr)map.put(ch,map.getOrDefault(ch,0)+1);
        PriorityQueue<Pair>pq=new PriorityQueue<>(
            new Comparator<Pair>()
            {
                public int compare(Pair a,Pair b)
                {
                    return b.freq-a.freq;
                }
            }
        );
        for(char key:map.keySet())pq.offer(new Pair(key,map.get(key)));
        int i=0;
        while(!pq.isEmpty())
        {
            Pair p=pq.poll();
            Arrays.fill(chr,i,i+p.freq,p.ch);
            i+=p.freq;
        }
        return String.valueOf(chr);
    }
    class Pair
    {
        char ch;
        int freq;
        public Pair(char ch,int freq)
        {
            this.freq=freq;
            this.ch=ch;
        }
    }
}
