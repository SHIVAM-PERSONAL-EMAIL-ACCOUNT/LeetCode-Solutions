### Solution

```java
class Solution {
    
    public boolean validMountainArray(int [] arr) {
        if (arr.length < 3)
            return false;
        
        int inflectionPoint = 0;
        
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] <= arr[i - 1]) {
                inflectionPoint = i - 1;
                break;
            }
        }
        
        if (inflectionPoint == 0)
            return false;
        
        for (int i = inflectionPoint + 1; i < arr.length; i++) {
            if (arr[i] >= arr[i - 1])
                return false;
        }
        
        return true;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
