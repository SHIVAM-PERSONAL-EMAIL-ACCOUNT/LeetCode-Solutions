### Solution

```java
class Solution {
    
    Map<Integer, Integer> permutationCache;
    
    public int numTrees(int n) {
        permutationCache = new HashMap<>();
        return calculate(1, n);
    }
    
    public int calculate(int start, int end) {
        if (start < 1 || start > end) return 1;
        if (permutationCache.containsKey(end - start + 1)) return permutationCache.get(end - start + 1);
        int permutations = 0;
        for(int i = start; i <= end; i++)
            permutations += calculate(start, i - 1) * calculate(i + 1, end);
        permutationCache.put(end - start + 1, permutations);
        return permutations;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(n)
