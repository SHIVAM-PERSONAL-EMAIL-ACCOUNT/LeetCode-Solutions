### Solution

```java
class Solution {
    
    int [][] visitedLand;
    
    public int numIslands(char [][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        
        initializeVisitedLandMatrix(m, n);
        int islands = 0;
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                char element = grid[i][j];
                if (element == '1' && visitedLand[i][j] == 0) {
                    explore(i, j, m, n, grid);
                    islands++;
                }
            }
        }
        
        return islands;
    }
    
    public void explore(int i, int j, int m, int n, char [][] grid) {
        visitedLand[i][j] = 1;
        if (j + 1 < n && grid[i][j + 1] == '1' && visitedLand[i][j + 1] == 0) explore(i, j + 1, m, n, grid);
        if (i + 1 < m && grid[i + 1][j] == '1' && visitedLand[i + 1][j] == 0) explore(i + 1, j, m, n, grid);
        if (j - 1 >= 0 && grid[i][j - 1] == '1' && visitedLand[i][j - 1] == 0) explore(i, j - 1, m, n, grid);
        if (i - 1 >= 0 && grid[i - 1][j] == '1' && visitedLand[i - 1][j] == 0) explore(i - 1, j, m, n, grid);
    }
    
    public void initializeVisitedLandMatrix(int m, int n) {
        visitedLand = new int [m][n];
    }
}
```

### Time/Space Complexity

- Time Complexity: O(mn)
- Space Compelxity: O(mn)
