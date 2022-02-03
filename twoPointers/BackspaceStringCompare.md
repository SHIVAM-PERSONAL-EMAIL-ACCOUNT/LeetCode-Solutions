### Solution

```java
class Solution {
    
    public boolean backspaceCompare(String s, String t) {
        Deque<Character> ss = new ArrayDeque<>();   
        Deque<Character> tt = new ArrayDeque<>(); 
        
        for (int i = 0 ; i < s.length(); i++) {
            if (s.charAt(i) == '#') {
                if (!ss.isEmpty()) ss.pop();
            }
            else ss.push(s.charAt(i));
        }
        
        for (int i = 0 ; i < t.length(); i++) {
            if (t.charAt(i) == '#') {
                if (!tt.isEmpty()) tt.pop();
            }
            else tt.push(t.charAt(i));
        }
        
        while (!ss.isEmpty() && !tt.isEmpty())
            if ((char)ss.pop() != (char)tt.pop()) return false;
        
        return ss.size() == tt.size();
    }
}
```

### Time/Space Complexity

- Time Complexity: O(m + n)
- Space Complexity: O(m + n)
