### Solution

```java
class Solution {
    
    public int minCostToMoveChips(int [] position) {
        int maxPos = 0, chipsAtLastPos = 0, chipsAtSecondLastPos = 0; 
        
        for (int pos : position)
            if (pos > maxPos)
                maxPos = pos;
        
        for (int pos : position)
            if((maxPos - pos) % 2 == 0)
                chipsAtLastPos++;
            else
                chipsAtSecondLastPos++;
        
        return Math.min(chipsAtLastPos, chipsAtSecondLastPos);
    }
}
```

### Time/Space Complexity:

- Time Complexity: O(n) where `n` is the length of the `position` array
- Space Complexity: O(1)
