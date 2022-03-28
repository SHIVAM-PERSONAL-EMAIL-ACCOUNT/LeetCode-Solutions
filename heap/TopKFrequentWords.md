### Solution

```java
class Solution {
    
    public List<String> topKFrequent(String [] words, int k) {
        List<String> res = new LinkedList<>();
        Map<String,Integer> map = new HashMap<>();
        PriorityQueue<Pair<Integer,String>> pq = new PriorityQueue<>(
            (p1,p2) -> {
                if (p1.getKey() == p2.getKey())
                    return p2.getValue().compareTo(p1.getValue());
                return p1.getKey() - p2.getKey();
            }
        );
        
        for (String word : words)
            map.put(word, map.getOrDefault(word,0) + 1);
        
        for (String key : map.keySet()) {
            pq.offer(new Pair(map.get(key),key));
            if (pq.size() > k) pq.poll();
        }
        
        while (k-- > 0)
            res.add(0, pq.poll().getValue());
        
        return res;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log k)
- Space Complexity: O(k)
