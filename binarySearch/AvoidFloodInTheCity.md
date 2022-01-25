### Solution

```java
class Solution {
    
    public int [] avoidFlood(int [] rains) {
        int ans [] = new int [rains.length];
        TreeSet<Integer> dryDays = new TreeSet<>();
        HashMap<Integer, Integer> fullLakes = new HashMap<>();
        
        for (int i = 0; i < rains.length; i++) {
            if (rains[i] == 0)
                dryDays.add(i);
            
            if (rains[i] > 0) {
                if (!fullLakes.containsKey(rains[i])) {
                    fullLakes.put(rains[i], i);
                }
                else {
                    Integer dryDay = dryDays.higher(fullLakes.get(rains[i]));
                    if (dryDay == null || dryDay > i) return new int [0];
                    ans[dryDay] = rains[i];
                    fullLakes.put(rains[i], i);
                    dryDays.remove(dryDay);
                }
                ans[i] = -1;
            }
        }
        
        while (!dryDays.isEmpty()) {
            ans[dryDays.pollFirst()] = 1;
        }
        
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(1)
