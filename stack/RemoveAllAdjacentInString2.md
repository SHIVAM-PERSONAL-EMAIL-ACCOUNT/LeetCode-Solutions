### Solution

```java
class Solution {
    
    public String removeDuplicates(String s, int k) {
        Deque<Pair<Character, Integer>> stack = new ArrayDeque<>();
        int length = s.length(); 
        int i = 0;
        while (i < length) {
            char currCh = s.charAt(i);
            int freq = (!stack.isEmpty() && stack.peek().getKey() == currCh) ? stack.pop().getValue() + 1 : 1;
            stack.push(new Pair(currCh, freq));
            if (stack.peek().getValue() == k) stack.pop();
            i++;
        }
        StringBuilder sb = new StringBuilder();
        while (!stack.isEmpty()) {
            Pair<Character, Integer> pair = stack.pollLast();
            for (i = 0; i < pair.getValue(); i++)
                sb.append(pair.getKey());
        }
        return sb.toString();
    }
}
```

### Time/Space Compelxity

- Time Compelxity: O(n)
- Space Compelxity: O(n)
