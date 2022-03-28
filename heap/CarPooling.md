### Solution

```
class Solution {
    
    public boolean carPooling(int [][] trips, int capacity) {
        Arrays.sort(trips, (t1,t2) -> t1[1] - t2[1]);
        PriorityQueue<int[]> pq = new PriorityQueue<>((t1,t2) -> t1[2] - t2[2]);
        for (int [] trip : trips) {
            capacity -= trip[0];
            while(!pq.isEmpty() && pq.peek()[2] <= trip[1])
                capacity += pq.poll()[0];
            if (capacity < 0) return false;
            pq.offer(trip);
        }
        return true;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(n)
