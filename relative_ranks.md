# May-8
## 506.Relative Ranks
```java
class Solution {
    public String[] findRelativeRanks(int[] score) {
        int n = score.length;
        String ans[] = new String[n];
        PriorityQueue<Pair> pq = new PriorityQueue<>(new Comparator<Pair>() {
            public int compare(Pair a, Pair b) {
                return b.val - a.val;
            }
        });
        for (int i = 0; i < n; i++)
            pq.offer(new Pair(score[i], i));
        int count = 0;
        while (!pq.isEmpty()) {
            count++;
            int ind = pq.poll().ind;
            if (count > 3) {
                ans[ind] = String.valueOf(count);
            } else {
                switch (count) {
                    case 1:
                        ans[ind] = "Gold Medal";
                        break;
                    case 2:
                        ans[ind] = "Silver Medal";
                        break;
                    case 3:
                        ans[ind] = "Bronze Medal";
                        break;

                }
            }
        }
        return ans;
    }

    class Pair {
        int val, ind;

    public Pair(int val,int ind)
        {
            this.val=val;
            this.ind=ind;
        }
    }
}
