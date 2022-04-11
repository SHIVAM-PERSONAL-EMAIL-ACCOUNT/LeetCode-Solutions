### Solution

```java
class Solution {
    
    public String longestCommonPrefix(String [] strs) {
        String string = strs[0];
        int match = string.length();
        for (String str : strs) {
            match = Math.min(match, str.length());
            for (int i = 0; i < match; i++) {
                if (str.charAt(i) != string.charAt(i)) {
                    match = i;
                    break;
                }
            }
            if (match == 0) return "";
        }
        return string.substring(0, match);
    }
}
```
### Assumption of Time/Space Complexity

`n` is the length of the `strs` array and `m` denotes length of strings in the array

### Time/Space Complexity

- Time Complexity: O(n * Math.min(m))
- Space Complexity: O(n)
