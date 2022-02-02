### Solution

```java
class Solution {
    
    public int countBinarySubstrings(String s) {
        int count = 1, total = 0, i = 1, j, len = s.length();
        char curr = s.charAt(0);
        
        while (i < len) {
            if (s.charAt(i) != curr) break;
            i++;
            count++;
        }
        
        if (i < len) curr = s.charAt(i);
        
        while (i < len) {
            j = i;
            while (j < len && count > 0) {
                if (s.charAt(j) != curr) break;
                j++;
                count--;
            }
            count = (j - i);
            total += count;
            while (j < len && s.charAt(j) == curr) {
                count++;
                j++;
            }
            i = j;
            if (i < len) curr = s.charAt(i);
        }
        
        return total;
    }
}
```

### Time/Sapce Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
