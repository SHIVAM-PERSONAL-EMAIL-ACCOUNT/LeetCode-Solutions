### Solution

```java
class Solution {
    
    public int [] diStringMatch(String s) {
        int ans [] = new int [s.length() + 1];
        int i = 0, j = s.length();
        for (int k = 0; k < s.length(); k++) {
            char ch = s.charAt(k);
            if (ch == 'I') ans[k] = i++;
            else ans[k] = j--;
        }
        ans[ans.length - 1] = i;
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1) (No extra space used other than the space required for answer array)
