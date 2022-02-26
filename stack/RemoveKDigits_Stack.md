### Solution

```java
class Solution {
    
    public String removeKdigits(String num, int k) {
        if (num.length() == k) return "0";
        Deque<Integer> stack = new ArrayDeque<>();
        int popped = 0;
        for(char alpha : num.toCharArray()) {
            while (!stack.isEmpty() && stack.peek() > (alpha - '0') && popped < k) {
                stack.pop();
                popped++;
            }
            stack.push(alpha - '0');
        }
        while (popped < k) {
            stack.pop();
            popped++;
        }
        StringBuilder sb = new StringBuilder();
        while (!stack.isEmpty() && stack.peekLast() == 0)
            stack.pollLast();
        while (!stack.isEmpty())
            sb.append(stack.pollLast());
        return sb.length() == 0 ? "0" : sb.toString();
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Compelxity: O(n)
