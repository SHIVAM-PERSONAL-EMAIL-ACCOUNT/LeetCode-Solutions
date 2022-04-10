### Solution

```java
class Solution {
    
    static class Structure {
        int elevation;
        int index;
        
        public Structure(int elevation, int index) {
            this.elevation = elevation;
            this.index = index;
        }
    }
    
    public int trap(int [] height) {
        int rainwaterTrapped = 0;
        int h = height.length;
        Deque<Structure> stack = new ArrayDeque<>();
        for (int i = 0; i < h; i++) {
            if (height[i] == 0) 
                continue;
            int alreadyIncludedElevation = 0;
            while(!stack.isEmpty() && stack.peek().elevation <= height[i]) {
                Structure shortStructure = stack.pop();
                rainwaterTrapped += (shortStructure.elevation - alreadyIncludedElevation) * (i - shortStructure.index - 1);
                alreadyIncludedElevation = shortStructure.elevation;
            }
            if(!stack.isEmpty()) {
                rainwaterTrapped += (height[i] - alreadyIncludedElevation) * (i - stack.peek().index - 1);
            }
            stack.push(new Structure(height[i],i));
        }
        return rainwaterTrapped;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
