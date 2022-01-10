### Solution

```java
class Solution {
    
    public List<List<Integer>> shiftGrid(int [][] grid, int k) {
        int length = grid.length * grid[0].length;
        int [] arr = new int [length];
        int [] newArr = new int [length];
        List<List<Integer>> ans = new ArrayList<>();
        
        int i = 0;
        for (int [] nums : grid)
            for (int num : nums)
                arr[i++] = num;
        
        i = length - k % length;
        
        int j = 0;
        while (i < length)
            newArr[j++] = arr[i++];
        
        i = 0;
        while (j < length)
            newArr[j++] = arr[i++];
        
        k = 0;
        for (i = 0; i < grid.length; i++) {
            List<Integer> list = new ArrayList<>();
            for (j = 0; j < grid[0].length; j++) {
                list.add(newArr[k++]);
            }
            ans.add(list);
        }
        
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n) where `n` is the total number of numbers in the `grid`
- Space Complexity: O(n)
