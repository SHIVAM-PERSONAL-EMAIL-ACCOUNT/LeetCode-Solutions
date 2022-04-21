### Solution

```java
class Solution {
    
    public int minPathSum(int [][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int [][] table = new int [m][n];
        for (int [] row : table)
            Arrays.fill(row, Integer.MAX_VALUE);
        table[0][0] = grid[0][0];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (i + 1 < m) table[i + 1][j] = Math.min(table[i + 1][j], table[i][j] + grid[i + 1][j]);
                if (j + 1 < n) table[i][j + 1] = Math.min(table[i][j + 1], table[i][j] + grid[i][j + 1]);
            }
        }
        return table[m - 1][n - 1];
    }
}
```
### Time/Space Complexity

- Time Complexity: O(m * n)
- Space Complexity: O(m * n)
