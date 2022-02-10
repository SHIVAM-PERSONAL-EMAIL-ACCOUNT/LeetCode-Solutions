### Solution

```java
class Solution {
    
    public int minimumDifference(int [] nums, int k) {
        Arrays.sort(nums);
        int min = Integer.MAX_VALUE;
        int i = k - 1;
        while (i < nums.length) {
            min = Math.min(min, nums[i] - nums[i - (k - 1)]);
            ++i;
        }
        return min;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(log n)
