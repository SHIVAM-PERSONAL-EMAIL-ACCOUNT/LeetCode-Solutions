### Solution

```java
class Solution {
    
    public int findSpecialInteger(int [] arr) {
        int candidate = -1, votes = 0;
        for (int num : arr)
            if (num == candidate)
                votes++;
            else
                if (votes > (arr.length/4))
                    return candidate;
                else {
                    candidate = num; votes = 1; }
        return candidate;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
