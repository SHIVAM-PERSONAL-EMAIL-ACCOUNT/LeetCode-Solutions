### Solution

```java
class Solution {
    
    public int characterReplacement(String s, int k) {
        int size = s.length();
        int maxSubstring = 0;
        for (int alpha = 1; alpha <= 26; alpha++) {
            int left = 0;
            int right = 0;
            int substitutions = 0;
            while (right < size) {
                char ch = s.charAt(right);
                if ((ch - 'A' + 1) != alpha) {
                    substitutions++;
                    if (substitutions > k) {
                        while ((s.charAt(left) - 'A' + 1) == alpha)
                            left++;
                        substitutions--;
                        left++;
                    }
                }
                right++;
                maxSubstring = Math.max(maxSubstring, right - left);
            }
        }
        return maxSubstring;
    }
}
```

### Time/Space Compelxity

- Time Compelxity: O(n)
- Space Compelxity: O(1)
