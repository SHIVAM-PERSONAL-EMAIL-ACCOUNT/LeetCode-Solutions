### Solution

```java
class Solution {
    
    public int countGoodSubstrings(String s) {
        int len = s.length(), count = 0;
        if (len < 3) return count;
        int [] duet = new int [2];
        duet[0] = s.charAt(0);
        duet[1] = s.charAt(1);
        int i = 2;
        while (i < len) {
            char ch = s.charAt(i);
            if (ch != duet[0] && ch != duet[1] && duet[0] != duet[1])
                ++count;
            duet[0] = duet[1];
            duet[1] = ch;
            ++i;
        }
        return count;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
