### Solution

```java
class Solution {
    
    public String minRemoveToMakeValid(String s) {
        Set<Integer> invalidIndices = getInvalidIndices(s);
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (!invalidIndices.contains(i))
                sb.append(c);
        }
        return sb.toString();
    }
    
    public Set<Integer> getInvalidIndices(String s) {
        Deque<Pair<Character, Integer>> stack = new ArrayDeque<>();
        Set<Integer> invalidIndices = new HashSet<>();
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (c == '(') 
                stack.push(new Pair(c, i));
            else if (c == ')')
                if (stack.isEmpty())
                    invalidIndices.add(i);
                else
                    stack.pop();
            else continue;
        }
        while (!stack.isEmpty())
            invalidIndices.add(stack.pop().getValue());
        return invalidIndices;
    }
}
```

### Time/Space Compelxity

- Time Complexity: O(n)
- Space Compelxity: O(n)
