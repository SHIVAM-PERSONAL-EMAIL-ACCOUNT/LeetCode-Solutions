### Solution

```java
class Solution {
    
    public int minStartValue(int [] nums) {
        int minSum = 1, tempSum = 0;
        for (int num : nums) {
            tempSum += num;
            if (tempSum < minSum) minSum = tempSum;
        }
        return (minSum == 1) ? 1 : 1 - minSum;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
