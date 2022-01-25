### Solution

```java
class Solution {
    
    public int minDays(int [] bloomDay, int m, int k) {
        if (m * k > bloomDay.length) return -1;
        
        int min = bloomDay[0], max = bloomDay[0];
        
        for (int bloomTime : bloomDay)
            if (bloomTime < min)
                min = bloomTime;
            else if (bloomTime > max)
                max = bloomTime;
        
        while (min < max) {
            int middle = min + (max - min)/2;
            int left = 0, bouquets = 0;
            for (int right = 0; right < bloomDay.length; right++) {
                if (bloomDay[right] > middle) {
                    left = right + 1;
                    continue;
                }
                if (right - left + 1 == k) {
                    left = right + 1;
                    bouquets++;
                    if (bouquets == m)
                        break;
                }
            }
            if (bouquets == m) max = middle;
            else min = middle + 1;
        }
        
        return min;
    }
}
```

## Time/Space Complexity:

- Time Complexity: O(n * log(max - min))
- Space Complexity: O(1)
