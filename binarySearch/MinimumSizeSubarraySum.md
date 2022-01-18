### Solution

```java
class Solution {
    
    public int minSubArrayLen(int target, int [] nums) {
        int i = 0, j = 0, total = 0, minSize = nums.length + 1, currSize; 
        
        outer: while (i < nums.length) {
            total += nums[i];
            
            if (total >= target) {
                currSize = i - j + 1;
              
                inner: while (j < i) {
                    total -= nums[j];  
                    if (total < target) {
                        total += nums[j];
                        break;
                    }
                    j++;
                    currSize--;
                } // inner ends
                
                if (currSize < minSize)
                    minSize = currSize;
                if (minSize == 1) return 1;
            } // "if (total >= target)" condition ends
            
            i++;
        } // outer ends
        
        return minSize == nums.length + 1 ? 0 : minSize;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
