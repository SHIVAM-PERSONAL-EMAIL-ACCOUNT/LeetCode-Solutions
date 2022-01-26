### Solution

```java
class Solution {
    
    public int minimumEffortPath(int [][] heights) {
        int  n = heights.length, m = heights[0].length;
        int min = 0, max = 0;
        
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (j - 1 >= 0) {
                    if (Math.abs(heights[i][j - 1] - heights[i][j]) > max)
                        max = Math.abs(heights[i][j - 1] - heights[i][j]);
                }    
                if (i - 1 >= 0) {
                    if (Math.abs(heights[i - 1][j] - heights[i][j]) > max)
                        max = Math.abs(heights[i - 1][j] - heights[i][j]);
                }
            }
        }
        
        while (min < max) {
            int middle = min + (max - min)/2;
            if (pathPossible(heights, middle, n, m)) max = middle;
            else min = middle + 1;
        }
        
        return min;
    }
    
    public boolean pathPossible(int [][] heights, int middle, int n, int m) {
        int [][] indices = new int [n][m];
        return start(0, 0, heights, indices, n, m, middle);
    }
    
    public boolean start(int i, int j, int [][] heights, int [][] indices, int n, int m, int k) {   
        if (i == n - 1 && j == m - 1)
            return true;
        
        indices[i][j] = 1;
        
        boolean path1, path2, path3, path4;
        path1 = path2 = path3 = path4 = false;
        
        if (i - 1 >= 0 && indices[i - 1][j] != 1) {
            if (Math.abs(heights[i - 1][j] - heights[i][j]) <= k)
                path1 = start(i - 1, j, heights, indices, n, m, k);
        }
        if (path1) return true;
        
        if (i + 1 < n && indices[i + 1][j] != 1) {
            if (Math.abs(heights[i + 1][j] - heights[i][j]) <= k)
                path2 = start(i + 1, j, heights, indices, n, m, k);
        }
        if (path2) return true;
        
        if (j - 1 >= 0 && indices[i][j - 1] != 1) {
            if (Math.abs(heights[i][j - 1] - heights[i][j]) <= k)
                path3 = start(i , j - 1, heights, indices, n, m, k);
        }
        if (path3) return true;
        
        if (j + 1 < m && indices[i][j + 1] != 1) {
            if (Math.abs(heights[i][j + 1] - heights[i][j]) <= k)
               path4 = start(i, j + 1, heights, indices, n, m, k);
        }
        if (path4) return true;
        
        return false;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n<sup>2</sup> * log(max))
- Space Complexity: O(n<sup>2</sup>)
