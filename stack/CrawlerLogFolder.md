### Solution

```java
class Solution {
    
    public int minOperations(String [] logs) {
        Deque<Integer> stack = new ArrayDeque<>();
        for (int i = 0; i < logs.length; i++) {
            String command = logs[i];
            if (command.equals("./"))
                continue;
            else if (!command.equals("../"))
                stack.push(1);
            else
                if (!stack.isEmpty()) 
                    stack.pop();
        }
        return stack.size();
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
