### Solution

```java
class Solution {
    
    public int lengthOfLongestSubstring(String string) {
        Set<Character> chars = new HashSet<>();
        int i, s, j, substring;
        substring = 0;
        s = string.length();
        i = j = 0;
        while (i < s) {
            char ch = string.charAt(i);
            while (chars.contains(ch) && j < i) {
                chars.remove(string.charAt(j));
                j++;
            }
            chars.add(ch);
            substring = Math.max(substring, i - j + 1);
            i++;
        }
        return substring;
    }
}
 ```
   
### Time/Space Complexity
   
- Time Complexity: O(n)
- Space Complexity: O(n)
