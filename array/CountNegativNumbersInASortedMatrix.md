### Solution

```java
class Solution {
    
    public int countNegatives(int [][] grid) {
        int count = 0;
        for (int [] row : grid) {
            int start = 0, end = row.length - 1, middle = 0, zeroes = 0;
            while (start <= end) {
                middle = (start + end)/2;
                if (row[middle] < 0) { zeroes = row.length - middle; end = middle - 1; }
                else start = middle + 1;
            }
            count += zeroes;
        }
        return count;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(1)
