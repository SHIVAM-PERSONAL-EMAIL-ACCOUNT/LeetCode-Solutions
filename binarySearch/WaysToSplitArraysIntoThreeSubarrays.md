### Solution

```java
class Solution {
    
    public int waysToSplit(int [] nums) {
        final int mod = 1000000007;
        final int n = nums.length;
        int preSum [] = new int [n];
        preSum[0] = nums[0];  
        for (int i = 1; i < n; i++) {
            preSum[i] = preSum[i - 1] + nums[i];
        }
        final int total = preSum[n - 1];
        int ans = 0;
        for (int i = 0; i < n - 2; i++) {
            int count = 0, left = -1, right = -1;
            int start = i + 1;
            int end = n - 2;
            while (start <= end) {
                int middle = (start + end)/2;
                if (preSum[middle] < 2 * preSum[i]) start = middle + 1;
                else { left = middle; end = middle - 1; }
            }
            if (left == -1) continue;
            start = i + 1;
            end = n - 2;
            while (start <= end) {
                int middle = (start + end)/2;
                if (preSum[middle] - preSum[i] > total - preSum[middle]) end = middle - 1;
                else { right = middle; start = middle + 1; }
            }
            if (right == -1) continue;
            count = right - left + 1;
            if (count > 0) ans = (ans + count) % mod;
        }
        return ans;
    }
}
```

## Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(n)
