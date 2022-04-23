### Solution

```java
class Solution {
    
    public int numDecodings(String str) {
        int s = str.length();
        int [] table = new int [s + 1];
        table[0] = 1;
        table[1] = str.charAt(0) == '0' ? 0 : 1;
        for (int i = 2; i < s + 1; i++) {
            char curr = str.charAt(i - 1);
            char prev = str.charAt(i - 2);
            int twoDigitNum = (prev - '0') * 10 + (curr - '0');
            table[i] = curr == '0' ? 0 : table[i - 1];
            table[i] += (prev == '0' || twoDigitNum > 26) ? 0 : table[i - 2]; 
        }
        return table[s];
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
