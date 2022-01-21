### Solution

```java
class Solution {
    
    public boolean judgeSquareSum(int c) {
        long low, high, middle, test;
        
        for (long i = (int) Math.sqrt(c); i >= 1; i--) {      
            low = 0;
            high = i;
            while (low <= high) {
                middle = low + (high - low)/2;
                test = i * i + middle * middle;
                if (test == c) return true;
                else if (test > c) high = middle - 1;
                else low = middle + 1;
            }
        }
        
        return false;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(c<sup>1/2</sup>log(c<sup>1/2</sup>))
- Space Complexity: O(1)
