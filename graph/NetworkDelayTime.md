### Solution

```java
class Solution {
    
    public int networkDelayTime(int [][] times, int n, int k) {
        int delay = 0;
        Set<Integer> visited = new HashSet<>();
        List<List<int[]>> graph = new ArrayList<>();
        Queue<int[]> pq = new PriorityQueue<>(Comparator.comparingInt(e -> e[1]));
        
        for (int i = 0; i < n; i++)
            graph.add(new ArrayList<>());
        
        for (int [] time : times)
            graph.get(time[0] - 1).add(new int [] {time[1] - 1, time[2]});
        
        pq.offer(new int [] {k - 1, 0});
        
        while(!pq.isEmpty()) {
            int [] source = pq.poll();
            if (visited.contains(source[0])) continue;
            int node = source[0];
            int time = source[1];
            visited.add(node);
            delay = Math.max(delay, time);
            for (int [] neighbour : graph.get(node))
                pq.offer(new int [] {neighbour[0], neighbour[1] + time});
        }
        
        return visited.size() == n ? delay : -1;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n + e + e * log(e))
- Space Complexity: O(n + e)
