### Solution

```java
class Solution {
    
    public boolean canReach(int [] arr, int start) {
        int [] visited = new int [arr.length];
        return DFS(arr, start, visited);
    }
    
    public boolean DFS(int [] arr, int start, int [] visited) {
        Deque<Integer> indexStack = new ArrayDeque<>();
        
        indexStack.add(start);
        
        while (!indexStack.isEmpty()) {
            int currIndex = indexStack.poll();
            visited[currIndex] = 1;
            
            if (arr[currIndex] == 0) return true;
            
            if (currIndex + arr[currIndex] < arr.length && visited[currIndex + arr[currIndex]] != 1)
                indexStack.add(currIndex + arr[currIndex]);
            
            if (currIndex - arr[currIndex] >= 0 && visited[currIndex - arr[currIndex]] != 1)
                indexStack.add(currIndex - arr[currIndex]);           
        }
        
        return false;
    }
}
```

### Time/Space Complexity:

- Time Complexity: O(n)
- Space Complexity: O(n)
