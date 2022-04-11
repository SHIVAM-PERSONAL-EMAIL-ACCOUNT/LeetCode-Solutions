### Solution

```java
class Solution {
    
    public int [][] diagonalSort(int [][] mat) {
        Queue<Integer> pq;
        int m = mat.length;
        int n = mat[0].length;
        
        int i = 0;
        while (i < m) {
            pq = new PriorityQueue<>();
            int row = i, col = 0;
            while (row < m && col < n) {
                pq.offer(mat[row][col]);
                row++;
                col++;
            }
            row = i; col = 0;
            while (!pq.isEmpty())
                mat[row++][col++] = pq.poll();
            i++;
        }
        
        i = 1;
        while (i < n) {
            pq = new PriorityQueue<>();
            int row = 0, col = i;
            while (row < m && col < n) {
                pq.offer(mat[row][col]);
                row++;
                col++;
            }
            row = 0; col = i;
            while (!pq.isEmpty())
                mat[row++][col++] = pq.poll();
            i++;
        }
        
        return mat;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n<sup>2</sup> * log(n))
- Space Complexity: O(n)
