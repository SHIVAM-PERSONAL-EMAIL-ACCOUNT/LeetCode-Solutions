### Solution

```java
class Solution {
    
    public int [] findRightInterval(int [][] intervals) {
        int i = 0, j, maxStart = intervals[0][0]; 
        
        int [] ans = new int [intervals.length];
        Map<Integer, Integer> map = new HashMap<>();
        
        for (int [] interval : intervals)
            map.put(interval[0], i++);
        
        for (int [] interval : intervals)
            if (interval[0] > maxStart)
                maxStart = interval[0];
        
        for (i = 0; i < intervals.length; i++) {
            if (intervals[i][0] == intervals[i][1]) {
                ans[i] = i;
            }
            else if (intervals[i][1] > maxStart) {
                ans[i] = -1;
            }
            else { 
                for (j = intervals[i][1]; j <= maxStart; j++) {
                    if (map.containsKey(j)) {
                        ans[i] = map.get(j);
                        break;
                    }
                }
            }
        }
        
        return ans;
    }
}
```
### Time/Space Complexity

- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(n)
