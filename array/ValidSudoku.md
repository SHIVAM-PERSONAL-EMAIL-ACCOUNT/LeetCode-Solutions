### Solution

```java
class Solution {
    
    /*
    1. Initialize 3 matrices:
        - One keeps tracks of all the elements in all the rows
        - Second Keeps tracks of all the elements in all the columns
        - Third Keeps tracks of all the elements in all the sub-boxes
    2. Traverse the matrix and insert all the elements in the three matrices at their right positions
        2.a. If the spot is already occupied in any matrix, return FALSE
    3. return TRUE
    */
    public boolean isValidSudoku(char [][] board) {
        int [][] rowMatrix = new int [9][9];
        int [][] colMatrix = new int [9][9];
        int [][] boxMatrix = new int [9][9];
        
        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {              
                if (board[i][j] == '.') continue;
                
                int piece = board[i][j] - '1';
                                
                // put piece in the row matrix
                if (rowMatrix[i][piece] != 0) return false;
                else rowMatrix[i][piece]++;
                
                // put piece in the col matrix
                if (colMatrix[j][piece] != 0) return false;
                else colMatrix[j][piece]++;
                
                // put piece in the box matrix
                int boxIndex;
                // boxIndex will be computed by the summation of the rowIndex and the colIndex
                if (i <= 2) boxIndex = 0;
                else if (i >= 3 && i <= 5) boxIndex = 1;
                else boxIndex = 2;
                if (j <= 2) boxIndex += 0;
                else if (j >= 3 && j <= 5) boxIndex += 3;
                else boxIndex += 6;
                
                if (boxMatrix[boxIndex][piece] != 0) return false;
                else boxMatrix[boxIndex][piece]++;
            }
        }
        
        return true;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(1)
- Space Complexity: O(1)
