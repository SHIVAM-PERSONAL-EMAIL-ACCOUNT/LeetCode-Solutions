### Solutions

```java
class Solution {
    
    public List<Integer> partitionLabels(String string) {
        Map<Character, Integer> map = new HashMap<>(); 
        List<Integer> res = new ArrayList<>();
        int windowStart, windowEnd, count;
        int s = string.length();
        
        // get the furthest index of each alphabet present in the string; the maximum size map can have is 26
        for (int i = 0; i < s; i++)
            map.put(string.charAt(i), i);
        
        windowStart = 0; 
        windowEnd = windowStart;
        count = 1; // keeps track of the size of the current window
        while (windowStart < s) {
            char ch = string.charAt(windowStart);
            // if the index of the current element exceeds the current window size ...
            if (map.get(ch) > windowEnd) {
                // increase the window size
                windowEnd = map.get(ch);
            }
            // if the index of current element is equal to the current window size and our loop pointer is at the window end ...
            else if (map.get(ch) == windowEnd && windowStart == windowEnd) {
                // add the window size to the result ...
                res.add(count);
                // and reset the parameters for the next window
                count = 0;
                windowEnd = windowStart + 1;
            }
            /*
            We are adding windowStart == windowEnd in the above condition for a case like "aaa". Here, we need to make sure that our pointer is
            at the window end. 
            
            We need not check for windowStart < windowEnd.
            */
            windowStart++;
            count++;
        }
        
        return res;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
