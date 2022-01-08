### Solution

```java
class Solution {
    
    public boolean canThreePartsEqualSum(int [] arr) {
        int total = 0;
        for (int num : arr)
            total += num;
        
        if (total % 3 != 0) return false;
        
        total /= 3;
        int sum = 0, counter = 0;
        for (int num : arr) {
            sum += num;
            if (sum == total) {
                counter++;
                sum = 0;
            }
        }
        
        return (counter >= 3) ? true : false;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
