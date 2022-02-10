### Solution

```java
class Solution {
    
    public String [] findRelativeRanks(int [] score) {
        String [] ranks = new String [score.length];
        PriorityQueue<Integer []> pq = new PriorityQueue<>((a,b) -> b[0] - a[0]);
        for (int i = 0; i < score.length; i++) {
            pq.offer(new Integer [] {score[i], i});
        }
        int i = 1;
        while (!pq.isEmpty()) {
            Integer [] temp = pq.poll();
            if (i == 1)
                ranks[temp[1]] = "Gold Medal";
            else if (i == 2)
                ranks[temp[1]] = "Silver Medal";
            else if (i == 3)
                ranks[temp[1]] = "Bronze Medal";
            else
                ranks[temp[1]] = Integer.toString(i);
            ++i;
        }
        return ranks;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(n)
