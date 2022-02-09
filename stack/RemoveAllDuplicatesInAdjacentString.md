### Solution

```java
class Solution {
    
    public String removeDuplicates(String s) {
        Deque<Character> stack = new ArrayDeque<>();
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (stack.isEmpty()) stack.push(ch);
            else
                if (stack.peek() != ch) stack.push(ch);
                else stack.pop();
        }
        StringBuilder str = new StringBuilder("");
        while(!stack.isEmpty())
            str.append(stack.pop());
        return str.reverse().toString();
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
