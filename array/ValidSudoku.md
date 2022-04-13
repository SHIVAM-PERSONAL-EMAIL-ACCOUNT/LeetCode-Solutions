### Solution

```java
class Solution {
    
    public boolean isValidSudoku(char [][] board) {
        Set<Integer> set;
        Map<Integer,Integer> rowMap = new HashMap<>();
        rowMap.put(0,0);
        rowMap.put(1,0);
        rowMap.put(2,0);
        rowMap.put(3,1);
        rowMap.put(4,1);
        rowMap.put(5,1);
        rowMap.put(6,2);
        rowMap.put(7,2);
        rowMap.put(8,2);
        Map<Integer,Integer> colMap = new HashMap<>();
        colMap.put(0,0);
        colMap.put(1,0);
        colMap.put(2,0);
        colMap.put(3,3);
        colMap.put(4,3);
        colMap.put(5,3);
        colMap.put(6,6);
        colMap.put(7,6);
        colMap.put(8,6);
        Set<Integer> [] blockSets = new HashSet [9];
        for (int i = 0; i < 9; i++)
           blockSets[i] = new HashSet<>();
        
        
        for (int i = 0; i < 9; i++) {
            set = new HashSet<>();
            for (int j = 0; j < 9; j++) {
                if (board[i][j] != '.' && !set.add(board[i][j] - '0')) {
                    return false;
                }
            }
        }
        
        for (int i = 0; i < 9; i++) {
            set = new HashSet<>();
            for (int j = 0; j < 9; j++) {
                if (board[j][i] != '.' && !set.add(board[j][i] - '0')) {
                    return false;
                }
            }
        }
        
        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                int blockCode = rowMap.get(i) + colMap.get(j);
                if (board[i][j] != '.' && !blockSets[blockCode].add(board[i][j] - '0')) {
                    return false;
                }
            }
        }
        
        return true;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(1)
- Space Complexity: O(1)
