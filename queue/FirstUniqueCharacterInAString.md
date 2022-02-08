### Solution

```java
class Solution {
    
    public int firstUniqChar(String s) {
        int [] freq = new int [26];
        int [] firstIndex = new int [26];
        Arrays.fill(firstIndex, -1);
        for (int i = 0; i < s.length(); i++) {
            int j = s.charAt(i) - 'a';
            if (firstIndex[j] == -1) firstIndex[j] = i;
            freq[j]++;
        }
        int ans = s.length() + 1;
        for (int i = 0; i < 26; i++)
           if (freq[i] == 1)
               if (firstIndex[i] < ans)
                   ans = firstIndex[i];
        return ans == s.length() + 1 ? -1 : ans;
    }
}
```

### Time/Space Compelxity

- Time Complexity: O(n)
- Space Compelxity: O(1)
