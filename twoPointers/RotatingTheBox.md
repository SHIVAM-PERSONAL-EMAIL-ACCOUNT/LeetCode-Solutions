### Solution

```java
class Solution {
    
    public char [][] rotateTheBox(char [][] box) {
        int row, rows, emptyLevel, currLevel, bottomLevel;
        
        rows = box.length;
        bottomLevel = box[0].length - 1;
        for (row = 0; row < rows; row++) {
            // we start to check from the bottom floor ...
            emptyLevel = bottomLevel;
            currLevel = emptyLevel - 1;
            outer: while (emptyLevel > 0) {
                // first we search for an empty floor where we can drop the stone
                while (emptyLevel > 0 && box[row][emptyLevel] != '.')
                    emptyLevel--;
                // if there was no empty level
                if (emptyLevel == 0) 
                    break outer;
                currLevel = Math.min(currLevel, emptyLevel - 1);
                // then we check for a floor above this empty floor which has a stone
                while (currLevel >= 0 && box[row][currLevel] != '#') {
                    // if we found a blockade then no stone is falling in the empty place ...
                    if (box[row][currLevel] == '*') {
                        // so we restart the check from floor above this
                        emptyLevel = currLevel - 1;
                        continue outer;
                    }
                    currLevel--;
                }
                // if there we no rocks to be found
                if (currLevel < 0) 
                    break outer;
                // for an empty floor and a rock, we drop the rock by swapping them
                dropTheStone(box, currLevel, emptyLevel, row);
                // then we increment the counters for the next floor
                emptyLevel--;
                currLevel--;
            }
        }
        
        char [][] ans = new char [bottomLevel + 1][rows];
        for (int i = 0; i < rows; i++)
            for (int j = bottomLevel; j >= 0; j--)
                ans[j][rows - i - 1] = box[i][j];
        
        return ans;
    }  
        
    
    public void dropTheStone(char[][] box, int from, int to, int row) {
        char temp = box[row][from];
        box[row][from] = box[row][to];
        box[row][to] = temp;
    }
}
```

### Time/Space Compelxity

- Time Compleixty: O(m * n)
- Space Compelxity: O(m * n)
