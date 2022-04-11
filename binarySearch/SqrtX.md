### Solution

```java
class Solution {
    
    public int mySqrt(int x) {
        if (x == 0) return 0;
        int left = 1, right = x, ans = left;
        while (left <= right) {
            int mid = left + (right - left)/2;
            int div = x/mid;
            if (mid == div) return mid;
            else if (mid > div) right = mid - 1;
            else { ans = Math.max(ans, mid); left = mid + 1; }
        }
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(log n)
- Space Complexity: O(1)
