### Solution

```java
class Solution {

    public int findKthPositive(int [] arr, int k) {
        int trailingNum = 0, trailingMissingNums = 0, missingNumsHere = 0;
        
        for (int i = 0; i < arr.length; i++) {         
            missingNumsHere = (arr[i] - trailingNum) - 1;
            
            if (trailingMissingNums + missingNumsHere >= k) 
                break;
            
            trailingNum = arr[i];
            trailingMissingNums += missingNumsHere;
        }
        
        return trailingNum + Math.abs(k - trailingMissingNums);
    }
} 
```

### Time/Sapce Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
