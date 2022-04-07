### Solution

```java
class Solution {
    
    static class Island {
        int notCaptured;
        List<int[]> coordinates;
        
        public Island() {
            this.notCaptured = 0;
            this.coordinates = new LinkedList<>();        }
    }
    
    List<Island> islands;
    int [][] visited;
    int m;
    int n;
    
    public void solve(char [][] board) {
        m = board.length;
        n = board[0].length;
        visited = new int [m][n];
        islands = new LinkedList<>();
        
        for (int i = 0; i < m; i++)
            for (int j = 0; j < n; j++)
                if (board[i][j] == 'O' && visited[i][j] == 0) {
                    Island island = new Island();
                    traverseIsland(i, j, board, island);
                    islands.add(island);
                }
        
        for (Island island : islands)
            if (island.notCaptured == 0)
                for (int [] coordinate : island.coordinates)
                    board[coordinate[0]][coordinate[1]] = 'X';
    }
    
    public void traverseIsland(int x, int y, char [][] board, Island island) {
        if ( x == m ||
             x < 0 ||
             y == n ||
             y < 0 ||
             board[x][y] == 'X' ||
             visited[x][y] == 1) 
            return;
        
        if ( x == m - 1 ||
             x == 0 ||
             y == n - 1 ||
             y == 0) 
            island.notCaptured = 1;
        
        visited[x][y] = 1;
        island.coordinates.add(new int [] {x,y});
        
        traverseIsland(x + 1, y, board, island);
        traverseIsland(x - 1, y, board, island);
        traverseIsland(x, y + 1, board, island);
        traverseIsland(x, y - 1, board, island);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(m * n)
- Space Complexity: O(m * n)
