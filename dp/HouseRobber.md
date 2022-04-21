### Solution

```java
class Solution {
    
    public int rob(int [] nums) {
        int n = nums.length;
        
        int [] table = new int [n + 2];
        table[0] = 0;
        table[1] = 0;
        
        int [] max = new int [n + 2];
        max[0] = 0;
        max[1] = 0;
        
        for (int  i = 0; i < n; i++) {
            table[i + 2] = Math.max(nums[i], nums[i] + max[i]);
            max[i + 2] = Math.max(table[i + 2], max[i + 1]);
        }
        
        return Math.max(table[n], table[n + 1]);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
