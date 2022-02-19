### Solution

```java
class Solution {
    
    public int [] deckRevealedIncreasing(int [] deck) {
        int indices, d;
        int ans [];
        Queue<Integer> queue;
        
        queue = new ArrayDeque<>();
        d = deck.length;
        ans = new int [d];
        
        Arrays.sort(deck);
        
        indices = 0;
        while (indices < d)
            queue.add(indices++);
        
        for (int card : deck) {
            ans[queue.peek()] = card;
            queue.poll();
            if (!queue.isEmpty()) queue.add(queue.poll());
        }
        
        return ans;
    }
}
```

### Time/Space Compelxity

 - Time Complexity: O(n)
 - Space Compelxity: O(n)
