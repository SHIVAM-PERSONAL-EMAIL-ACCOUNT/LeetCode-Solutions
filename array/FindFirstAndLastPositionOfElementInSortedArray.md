### Solution

```java
class Solution {
    
    /*
    1. Find the index of the target through binary search
    2. If target not present, return [-1,-1]
    3. If target present:
        3.1. Binary search on the left half of the array for the left most index of the target
        3.2. Binary search on the right half of the array for the right most index of the target
    */
    public int [] searchRange(int [] nums, int target) {
        int start = 0, end = nums.length - 1, middle = 0;
        boolean found = false;
        
        while (start <= end) {
            middle = (start + end)/2;
            if (target == nums[middle]) { found = true; break; }
            else if (target > nums[middle]) start = middle + 1;
            else end = middle - 1;
        }
        
        if (!found) return new int [] {-1, -1};
        
        start = 0; end = nums.length - 1;
        int leftEnd = middle - 1, rightStart = middle + 1;
        
        while (start <= leftEnd) {
            middle = (start + leftEnd)/2;
            if (target == nums[middle]) leftEnd = middle - 1;
            else start = middle + 1;
        }
        
        while (rightStart <= end) {
            middle = (rightStart + end)/2;
            if (target == nums[middle]) rightStart = middle + 1;
            else end = middle - 1;
        }
        
        return new int [] {start, end};
    }
}
```

### Time/Space Complexity

- Time Complexity: O(log n)
- Space Compelxity: O(1)
