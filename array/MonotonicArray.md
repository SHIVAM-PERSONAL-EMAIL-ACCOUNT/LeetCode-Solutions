### Solution

```java
class Solution {
    
    public boolean isMonotonic(int [] nums) {
        boolean monotoneInc = true, monotoneDec = true;
        
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] < nums[i - 1]) {
                monotoneInc = false;
                break;
            }
        }
        
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > nums[i - 1]) {
                monotoneDec = false;
                break;
            }
        }
        
        return monotoneDec || monotoneInc;
    }
}
```
### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
