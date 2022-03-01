### Solution

```java
class Solution {
    
    public int maxChunksToSorted(int [] arr) {
        int len = arr.length;
        int chunks = 0;
        int i = 0;
        while (i < len) {
            if (arr[i] == i) {
                chunks++;
                i++;
            }
            else {
                int windowSize = arr[i];
                while (i <= windowSize) {
                    if (arr[i] > windowSize)
                        windowSize = arr[i];
                    i++;
                }
                chunks++;
            }
        }
        return chunks;
    }
}
```

### Time/Space Compelxity

- Time Compelxity: (n)
- Space Compelxity: O(1)
