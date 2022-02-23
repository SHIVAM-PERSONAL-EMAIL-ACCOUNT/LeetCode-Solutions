### Solution

```java
class Solution {
    
    public String simplifyPath(String path) {
        Deque<String> stack = new ArrayDeque<>();
        stack.push("/");
        
        int pathLength = path.length();
        String component = "";
        for (int i = 1; i < pathLength; i++) {
            char ch = path.charAt(i);
            if (ch == '/') {
                if (component.equals("")) continue;
                switch(component) {
                    case ".":
                        break;
                    case "..":
                        if (stack.size() == 1) break;
                        else { stack.pop(); stack.pop(); }
                        break;
                    default: 
                        stack.push(component);
                        stack.push("/");
                        break;
                }
                component = "";
                continue;
            }
            component += ch;
        }
        if (path.charAt(pathLength - 1) != '/' && !component.equals(".")) {
            if (component.equals("..")) {
                if (stack.size() != 1) { stack.pop(); stack.pop(); }
            }
            else stack.push(component);
        } 
        
        if (stack.size() != 1 && stack.peek().equals("/")) stack.pop();
        
        StringBuilder canonicalPath = new StringBuilder();
        while (!stack.isEmpty())
            canonicalPath.append(stack.pollLast());
        
        return canonicalPath.toString();
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
