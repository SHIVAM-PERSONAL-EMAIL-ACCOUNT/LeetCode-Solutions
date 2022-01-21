### Solution

```java
class Solution {
    
    public int minEatingSpeed(int [] piles, int h) {
        Arrays.sort(piles);
        int low = 1, high = piles[piles.length - 1], currRate, i, currPileHoursTaken, totalHoursTaken;
        while (low < high) {
            currRate = low + (high - low)/2;
            i = -1;
            totalHoursTaken = 0;
            for (i = piles.length - 1; i >= 0; i--) {
                if (currRate > piles[i]) 
                    break; 
                currPileHoursTaken = piles[i] / currRate;
                if (piles[i] % currRate != 0)
                    currPileHoursTaken++;
                totalHoursTaken += currPileHoursTaken;
                if (totalHoursTaken > h)
                    break;
            }
            if (i >= 0)
                totalHoursTaken += (i + 1);           
            if (totalHoursTaken > h) low = currRate + 1;
            else high = currRate;
        }
        return low;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n * log(m)), where `m` is the height of the pile of the maximum height
- Space Complexity: O(log(n))
