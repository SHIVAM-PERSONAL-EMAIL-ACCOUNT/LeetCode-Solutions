### Solution

```java
class Solution {
    
    int count = 0;
    int max = 0;
    int m = 0;
    int n = 0;
    int [][] visited;
    
    public int maxAreaOfIsland(int [][] grid) {
        m = grid.length;
        n = grid[0].length;
        visited = new int [m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 0 || visited[i][j] == 1)
                    continue;
                dfs(i, j, grid);
                max = Math.max(max, count);
                count = 0;
            }
        }
        return max;
    }
    
    public void dfs(int x, int y, int [][] grid) {
        if (x == m ||
            y == n ||
            x < 0 ||
            y < 0 ||
            grid[x][y] == 0 ||
            visited[x][y] == 1
        ) return;
        visited[x][y] = 1;
        count++;
        dfs(x + 1, y, grid);
        dfs(x - 1, y, grid);
        dfs(x, y + 1, grid);
        dfs(x, y - 1, grid);
    }
}
```

### Time/Space Coomplexity

- Time Complexity: O(m * n)
- Space Complexity: O(m * n)
