### Solution

```java
class Solution {
    
    public int orangesRotting(int [][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        
        Queue<int[]> coordinates = new LinkedList<>();
        
        for (int i = 0; i < m; i++)
            for (int j = 0; j < n; j++)
                if (grid[i][j] == 2)
                    coordinates.add(new int [] {i, j});
        
        int minutes = 0;
        
        while(!coordinates.isEmpty()) {
            int size = coordinates.size();
            for (int k = 0; k < size; k++) {
                int [] coordinate = coordinates.poll();
                int x = coordinate[0];
                int y = coordinate[1];
                if (x + 1 < m && grid[x + 1][y] == 1) {
                    grid[x + 1][y] = 2;
                    coordinates.add(new int [] {x + 1, y});
                }
                if (x - 1 >= 0 && grid[x - 1][y] == 1) {
                    grid[x - 1][y] = 2;
                    coordinates.add(new int [] {x - 1, y});
                }
                if (y + 1 < n && grid[x][y + 1] == 1) {
                    grid[x][y + 1] = 2;
                    coordinates.add(new int [] {x, y + 1});
                }
                if (y - 1 >= 0 && grid[x][y - 1] == 1) {
                    grid[x][y - 1] = 2;
                    coordinates.add(new int [] {x, y - 1});
                }
            }
            ++minutes;
        }
        
        for (int i = 0; i < m; i++)
            for (int j = 0; j < n; j++)
                if (grid[i][j] == 1)
                    return -1;
        
        return minutes == 0 ? minutes : minutes - 1;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(m * n)
- Space Complexity: O(m * n)
