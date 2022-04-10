### Solution

```java
class Solution {
    
    public int threeSumClosest(int [] nums, int target) {
        Arrays.sort(nums);
        int n = nums.length;
        int ans = 10000000;
        for (int i = 0; i < n - 2; i++) {
            int diff = target - nums[i];
            int start = i + 1, end = n - 1;
            while(start < end) {
                int sum = nums[start] + nums[end];
                if (sum == diff) return target;
                int potentialAns = nums[i] + nums[start] + nums[end];
                if (Math.abs(target - potentialAns) < Math.abs(target - ans)) ans = potentialAns;
                if (sum < diff) start++;
                else end--;
            }
        }
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(1)
