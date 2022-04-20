### Solution

```java
class Solution {
    
    public int minCostClimbingStairs(int [] cost) {
        int n = cost.length;
        int [] minCost = new int [n + 1];
        Arrays.fill(minCost, Integer.MAX_VALUE);
        minCost[0] = 0;
        minCost[1] = 0;
        for (int i = 0; i < n + 1; i++) {
            if (i + 1 < n + 1) minCost[i + 1] = Math.min(minCost[i + 1], minCost[i] + cost[i]);
            if (i + 2 < n + 1) minCost[i + 2] = Math.min(minCost[i + 2], minCost[i] + cost[i]);
        }
        return minCost[n];
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
