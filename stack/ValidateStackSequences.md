### Solution

```java
class Solution {
    
    public boolean validateStackSequences(int [] pushed, int [] popped) {
        Deque<Integer> pushStack = new ArrayDeque<>();
        int pushLen = pushed.length;
        int popLen = popped.length;
        int pushItr = 0;
        int popItr = 0;
        while (pushItr < pushLen) {
            pushStack.push(pushed[pushItr]);
            pushItr++;
            while (!pushStack.isEmpty() && popped[popItr] == pushStack.peek()) {
                pushStack.pop();
                popItr++;
            }
        }
        return popItr == popLen;
    }
}
```

### Time/Space Compelxity

- Time Compelxity: O(n)
- Space Compelxity: O(n)
