# April-10
## 950. Reveal Cards in Increasing Order
```java
class Solution {
    public int[] deckRevealedIncreasing(int[] deck) {
        Arrays.sort(deck);
        int n=deck.length;
        Queue<Integer> queue = new LinkedList<>();
        for(int i = n-1; i >= 0;i--) {
            if(queue.size() > 0)
                queue.add(queue.poll());
            queue.add(deck[i]);
        }

        for(int i =n-1; i >= 0; i--)
            deck[i] = queue.poll();

        return deck;
    }
}

