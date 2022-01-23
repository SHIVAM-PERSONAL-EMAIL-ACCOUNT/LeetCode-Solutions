### Solution

```java
class Solution {
    
    public int equalSubstring(String s, String t, int maxCost) {
        int left = 0, right = 0, cumCost = 0, maxLen = 0;
        while (right < s.length()) {
            int cost = Math.abs(s.charAt(right) - t.charAt(right));
            cumCost += cost;
            if (cumCost <= maxCost) {
                right++;
            }
            else {
                while (left < right && cumCost > maxCost) {
                    int tempCost = Math.abs(s.charAt(left) - t.charAt(left));
                    cumCost -= tempCost;
                    left++;
                }
                right++;
                if (cumCost > maxCost) {
                    left++;
                    cumCost = 0;
                }
            }
            maxLen = Math.max(maxLen, right - left);
        }
        return maxLen;
    }
}
```

### Time/Space Complexity:

- Time Complexity: O(n)
- Space Complexity: O(1)
