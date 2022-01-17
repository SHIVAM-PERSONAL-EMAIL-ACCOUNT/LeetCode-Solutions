### Solution

```java
class Solution {
    
    /*
    1. Sort the array
    2. For every number from maximum number to 1
        2.1. Find the last index where a number is greater than equal to that number
        2.2. If special condition satisfied, return special number
    3. Return -1 for no result
    */
    public int specialArray(int [] nums) {
        int target, left = 0, right = nums.length - 1, middle;
        
        Arrays.sort(nums);
        
        target = nums[nums.length - 1];
        
        while (target > 0) {
            while (left <= right) {
                middle = (left + right)/2;
                
                if (nums[middle] >= target) right = middle - 1;
                else left = middle + 1; 
            }
            
            if (nums.length - left == target)
                return target;
            
            right = left;
            left = 0;
            target--;
        }
        
        return -1;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity O(1)
