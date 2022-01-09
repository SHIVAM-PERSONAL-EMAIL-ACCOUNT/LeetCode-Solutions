### Solution

```java
class Solution {
    
    public int countCharacters(String [] words, String chars) {
        int [] charFreq = new int [26];
        
        for (char character : chars.toCharArray())
            charFreq[character - 'a']++;
        
        int sum = 0;
        outer: for (String word : words) {
            int [] tempFreq = Arrays.copyOf(charFreq, charFreq.length);
            inner: for (char character : word.toCharArray()) {
                if (tempFreq[character - 'a'] == 0)
                    continue outer;
                tempFreq[character - 'a']--;
            }
            sum += word.length();
        }
        
        return sum;
    }
}
```

### Assumption

For Complexity analysis, 'n` is the length of the `words` array, length of each `String` in the `array` and it is also the length of the 'chars`

### Time/Space Complexity

- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(n)
