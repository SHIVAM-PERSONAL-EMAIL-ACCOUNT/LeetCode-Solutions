### Solution

```java
class Solution {
    
    List<Integer> res;
    
    public List<Integer> spiralOrder(int[][] matrix) {
        res = new LinkedList<>();
        getBorders(0, matrix[0].length - 1, 0, matrix.length - 1, matrix);
        return res;
    }
    
    public void getBorders(int leftBound, int rightBound, int topBound, int bottomBound, int [][] matrix) {
        if (leftBound > rightBound || bottomBound < topBound)
            return;
        
        for (int i = leftBound; i <= rightBound; i++)
            res.add(matrix[topBound][i]);
        
        for (int i = topBound + 1; i <= bottomBound; i++)
            res.add(matrix[i][rightBound]);
        
        if (leftBound == rightBound || topBound == bottomBound)
            return;
        
        for (int i = rightBound - 1; i >= leftBound; i--)
            res.add(matrix[bottomBound][i]);
        
        for (int i = bottomBound - 1; i > topBound; i--)
            res.add(matrix[i][leftBound]);
        
        getBorders(leftBound + 1, rightBound - 1, topBound + 1, bottomBound - 1, matrix);
    }
}
```
### Time/Space Complexity

- Time Complexity: O(N) where `N` is the total numbers in the matrix
- Space Complexity: O(min(m,n))
