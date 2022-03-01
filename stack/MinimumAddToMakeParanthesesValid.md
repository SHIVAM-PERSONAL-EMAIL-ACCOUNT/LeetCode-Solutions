### Solution

```java
class Solution {
    
    public int minAddToMakeValid(String brackets) {
        Deque<Character> stack = new ArrayDeque<>();
        int moves = 0;
        for (char bracket : brackets.toCharArray()) {
            if (bracket == '(') 
                stack.push(bracket);
            else
                if (stack.isEmpty())
                   moves++;
                else
                    stack.pop();
        }
        return moves + stack.size();
    }
}
```
### Time/Space Compelxity

- Time Complexity: O(n)
- Space Complexity: O(n)
