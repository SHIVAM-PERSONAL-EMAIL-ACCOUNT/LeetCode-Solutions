### Solution

```java
class Solution {
    
    public String largestMerge(String word1, String word2) {        
        StringBuilder merge = new StringBuilder();
        int i1, i2, w1, w2;
        w1 = word1.length();
        w2 = word2.length();
        
        i1 = 0;
        i2 = 0;
        while (i1 < w1 || i2 < w2) {
            if (word1.substring(i1).compareTo(word2.substring(i2)) >= 0) {
                merge.append(word1.charAt(i1));
                i1++;
            }
            else {
                merge.append(word2.charAt(i2));
                i2++;
            }
        }
        
        return merge.toString();
    }
}
```

### Time/Space Compelxity

- Time Compelxity: O(m<sup>2</sup> + n<sup>2</sup>)
- Space Complexity: O(m<sup>2</sup> + n<sup>2</sup>)
