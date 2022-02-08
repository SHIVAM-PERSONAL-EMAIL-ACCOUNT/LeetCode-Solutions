### Solution

```java
class Solution {
    
    public int timeRequiredToBuy(int [] tickets, int k) {
        int seconds = 0;
        while_loop: while(true) {
            for (int i = 0; i < tickets.length; i++) {
                int ticket = tickets[i];
                if (ticket == 0) continue;
                tickets[i] = --ticket;
                if (ticket == 0)
                    if (i == k) break while_loop;
                ++seconds;
            }
        }
        return seconds + 1;
    }

}
```

### Time/Space Complexity

- Time Complexity: O(tickets[k] * tickets.length)
- Space Complexity: O(1)
