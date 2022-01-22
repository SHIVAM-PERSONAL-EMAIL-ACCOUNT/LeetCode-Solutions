### Solution

```java
class Solution {
    
    public int shipWithinDays(int [] weights, int days) {
        int maxWeight = 0, totalWeight = 0, min, max, middle, i, currCap, totalDays;
        
        for (int weight : weights) {
            if (weight > maxWeight)
                maxWeight = weight;
            totalWeight += weight;
        }
        
        min = maxWeight; 
        max = totalWeight;
        while (min < max) {
            middle = min + (max - min)/2;
            i = 0;
            currCap = 0;
            totalDays = 0;
            while (totalDays <= days && i < weights.length) {
                if (currCap + weights[i] >= middle) {
                    if (currCap + weights[i] == middle)
                        i++;
                    currCap = 0;
                    totalDays++;
                }
                else {
                    currCap += weights[i];
                    i++;
                }
            }
            if (currCap < totalWeight && currCap != 0) totalDays++;
            if (totalDays > days) min = middle + 1;
            else max = middle;
        }
        
        return min;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n * log(max))
- Space Complexity: O(1)
