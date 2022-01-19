### Solution

```java
class Solution {
    
    /*
    1. Binary Search in the first column to filter out rows that have nums greater than the target
    2. Binary Search in the last column to filter out rows that have nums less than the target
    3. Perform Binary Search in each filtered row 
    */
    public boolean searchMatrix(int [][] matrix, int target) {
        int left, right, middle, start, end, cols;
        
        left = 0; 
        right = matrix.length - 1;
        
        while (left <= right) {
            middle = (left + right)/2;
            
            if (matrix[middle][0] == target) return true;
            else if (matrix[middle][0] > target) right = middle - 1;
            else left = middle + 1;
        }
        
        end = Math.min(left, matrix.length - 1);
        
        cols = matrix[0].length;
        left = 0;
        right = matrix.length - 1;
        
        while (left <= right) {
            middle = (left + right)/2;
            
            if (matrix[middle][cols - 1] == target) return true;
            else if (matrix[middle][cols - 1] > target) right = middle - 1;
            else left = middle + 1;
        }
        
        start = Math.max(left, 0);
        
        for (int i = start; i <= end; i++) {
            
            left = 0;
            right = cols - 1;            
            while (left <= right) {
                middle = (left + right)/2;
            
                if (matrix[i][middle] == target) return true;
                else if (matrix[i][middle] > target) right = middle - 1;
                else left = middle + 1;
            }
        }
        
        return false;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n) where `n` is the rows, equals to columns, in the matrix in the worst case scenario
- Space Complexity: O(1)
