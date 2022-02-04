### Solution

```java
class Solution {
    
    public String reversePrefix(String word, char ch) {
        StringBuilder str = new StringBuilder(word);
        int i = 0;
        for (i = 0; i < word.length(); i++) {
            if (word.charAt(i) == ch) break;
        }
        if (i == word.length()) return word;
        reverse(i, str);
        return str.toString();
    }
    
    public void reverse(int till, StringBuilder str) {
        int i = 0;
        while (i < till) {
            char temp = str.charAt(i);
            str.setCharAt(i, str.charAt(till));
            str.setCharAt(till, temp);
            i++;
            till--;
        }
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
