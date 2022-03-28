### Solution

```java
class Solution {
    public String frequencySort(String s) {
        Map<Character, Integer> map = new HashMap<>();
        PriorityQueue<Integer[]> pq  = new PriorityQueue<>((a1,a2) -> a2[1] - a1[1]);
        StringBuilder res = new StringBuilder();
        
        for (char ch : s.toCharArray())
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        
        map.forEach((k,v) -> pq.offer(new Integer [] {(int)k, v}));
        
        while(!pq.isEmpty()) {
            Integer [] pair = pq.poll();
            char ch = (char)((int)pair[0]);
            int freq = pair[1];
            while (freq-- > 0)
                res.append(ch);
        }
        
        return res.toString();
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log k)
- Space Complexity: O(k)
