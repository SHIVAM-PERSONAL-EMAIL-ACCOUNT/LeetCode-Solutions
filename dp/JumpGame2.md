### Solution

```java
class Solution {
    
    public int jump(int [] nums) {
        int destination = nums.length - 1; 
        if (destination == 0) return 0;
        int jumps = 1;
        int maxWindowSize = Math.min(nums[0], destination);
        int j = 1;
        while (true) {
            if (maxWindowSize >= destination) break;
            int maxJump = maxWindowSize;
            while (j <= maxJump) {
                maxWindowSize = Math.max(maxWindowSize, j + nums[j]);
                j++;
            }
            jumps++;
        }
        return jumps;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
