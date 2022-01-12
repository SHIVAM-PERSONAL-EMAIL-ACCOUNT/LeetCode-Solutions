### Solution

```java
class Solution {
    
    public List<Integer> luckyNumbers (int [][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        
        if (m == 1 && n == 1) return new ArrayList(Arrays.asList(matrix[0][0]));
        
        Set<Integer> rowMin = new HashSet<>();
        Set<Integer> colMax = new HashSet<>();
        
        for (int i = 0; i < m; i++) {
            int min = matrix[i][0];
            for (int j = 1; j < n; j++) {
                if (matrix[i][j] < min) 
                    min = matrix[i][j];
            }
            rowMin.add(min);
        }
        
        for (int i = 0; i < n; i++) {
            int max = matrix[0][i];
            for (int j = 1; j < m; j++) {
                if (matrix[j][i] > max) 
                    max = matrix[j][i];
            }
            colMax.add(max);
        }
        
        List<Integer> ans = new ArrayList<>();
        
        if (m < n) {
            for (Integer num : rowMin)
                if (colMax.contains(num))
                    ans.add(num);
        }
        else {
            for (Integer num : colMax)
                if (rowMin.contains(num))
                    ans.add(num);
        }
        
        return ans;
    }
}
```

### Assumption

Under worst case scenario, `n` is the number of `rows` in the matrix which is equal to the number of `columns` in the matrix. 

### Time/Space Complexity

- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(n)
