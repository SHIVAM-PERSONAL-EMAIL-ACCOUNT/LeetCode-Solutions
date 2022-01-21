### Solution

```java
import java.util.*;

class Solution {
    
    public int maxProfitAssignment(int [] difficulty, int [] profit, int [] worker) {
        int currMaxProfit, lastMaxProfit = 0, totalProfit = 0, prevWorkerDifficultyLimit = 0;
        TreeMap<Integer, Integer> sortedMap = new TreeMap<>();
        
        for (int i = 0; i < difficulty.length; i++) {
            if (!sortedMap.containsKey(difficulty[i]))
                sortedMap.put(difficulty[i], profit[i]);
            else
                if (profit[i] > sortedMap.get(difficulty[i]))
                    sortedMap.put(difficulty[i], profit[i]);
        }
        
        Arrays.sort(worker);
        
        for (int currWorkerDifficultyLimit : worker) {
            NavigableMap<Integer, Integer> tailMap = sortedMap.tailMap(prevWorkerDifficultyLimit, true);
            currMaxProfit = 0;
            for (Integer currDifficulty : tailMap.keySet()) {
                if (currDifficulty > currWorkerDifficultyLimit)
                    break;
                if (currMaxProfit < tailMap.get(currDifficulty))
                    currMaxProfit = tailMap.get(currDifficulty);
            }
            totalProfit += Math.max(currMaxProfit, lastMaxProfit);
            if (currMaxProfit > lastMaxProfit) lastMaxProfit = currMaxProfit;
            prevWorkerDifficultyLimit = currWorkerDifficultyLimit;
        }
        
        return totalProfit;
    }
}
```

### Time/Space Compelxity

- Time Complexity: O(d * (log d)<sup>3</sup> + w * log w), where `d` is the length of the `difficulty` array and `w` is the length of the `worker` array
- Space Complexity: O(d)
