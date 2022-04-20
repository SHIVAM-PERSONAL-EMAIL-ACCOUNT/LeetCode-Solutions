### Solution

```java
class Solution {
    
    Map<Integer,Integer> map = new HashMap<>();
    
    public int climbStairs(int n) {
        if (map.containsKey(n)) return map.get(n);
        if (n == 0) return 1;
        if (n < 0) return 0;
        int res = climbStairs(n - 1) + climbStairs(n - 2);
        map.put(n, res);
        return res;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
