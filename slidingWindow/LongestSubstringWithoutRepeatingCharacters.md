### Solution

```java
class Solution {
    
    public int lengthOfLongestSubstring(String str) {
        int s = str.length();
        if (s == 0) return 0;
        if (s == 1) return 1;
        Set<Character> set = new HashSet<>();
        int maxLen = 1;
        int i = 0, j = 0;
        while (j < s) {
            char ch = str.charAt(j);
            while (set.contains(ch)) 
                set.remove(str.charAt(i++));
            set.add(ch);
            maxLen = Math.max(maxLen, j - i + 1);
            j++;
        }
        return maxLen;
    }
}
 ```
   
### Time/Space Complexity
   
- Time Complexity: O(n)
- Space Complexity: O(n)
