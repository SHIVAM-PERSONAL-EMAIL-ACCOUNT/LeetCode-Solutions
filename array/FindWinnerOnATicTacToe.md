### Solution

```java
class Solution {
    
    public String tictactoe(int [][] moves) {
        int [][] grid = new int [3][3];
        
        int j = -1;
        for (int [] move : moves)
            if(++j % 2 == 0)
                grid[move[0]][move[1]] = 1;
            else
                grid[move[0]][move[1]] = -1;
                
        int i;
        int test = grid[0][0] + grid[1][1] + grid[2][2];
        if (test == 3 || test == -3)
            return test == 3 ? "A" : "B";
        
        test = grid[0][2] + grid[1][1] + grid[2][0];
        if (test == 3 || test == -3)
            return test == 3 ? "A" : "B";
        
        for (i = 0; i < 3; i++) {
            test = grid[i][0] + grid[i][1] + grid[i][2];
            if (test == 3 || test == -3)
                return test == 3 ? "A" : "B";
            
            test = grid[0][i] + grid[1][i] + grid[2][i];
            if (test == 3 || test == -3)
                return test == 3 ? "A" : "B";
        }
            
        return j < 8 ? "Pending" : "Draw";
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n) where 'n' is the length of the `moves` array
- Sapce Complexity: O(1)
