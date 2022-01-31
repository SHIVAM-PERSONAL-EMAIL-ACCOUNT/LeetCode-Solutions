### Solution

```java
class Solution {
    
    public int maxDistance(int[] nums1, int[] nums2) {
        int n1 = nums1.length, n2 = nums2.length, ans = 0;
        if (n1 > n2) n1 = n2;
        for (int j = n2 - 1; j >= 0; j--) {
            if (j < n1 - 1) n1--;
            if (ans > j) break;
            if (nums2[j] < nums1[n1 - 1]) continue;
            int left = nums1Index(nums1, j, nums2[j]);
            if (left == -1) continue;
            ans = Math.max(ans, j - left);
        }
        return ans;
    }
    
    public int nums1Index(int [] nums1, int jThIndex, int value) {
        int left = 0, right = Math.min(jThIndex, nums1.length - 1), ans = -1;
        while (left <= right) {
            int middle = (left + right)/2;
            if (nums1[middle] > value) left = middle + 1;
            else { ans = middle; right = middle - 1; }
        }
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n2 log n2)
- Space Complexity: O(1)
