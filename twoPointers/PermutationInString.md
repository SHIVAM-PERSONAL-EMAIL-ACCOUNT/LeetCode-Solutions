### Solution

```java
class Solution {
    
    public boolean checkInclusion(String s1, String s2) {
        int [] alphas = new int [26];
        
        for (int i = 0; i < s1.length(); i++)
            alphas[s1.charAt(i) - 'a']++;
        
        int k = 0;
        while (k < s2.length()) {
            int temp [] = new int [26];
            for (int j = 0; j < 26; j++)
                temp[j] = alphas[j];
            
            int total = s1.length();
            int i = k;
            while (i < s2.length() && total > 0) {
                if (temp[s2.charAt(i) - 'a'] == 0) break;
                else {
                    temp[s2.charAt(i) - 'a']--;
                    i++;
                    total--;
                }
            }
            
            if (total == 0)
                return true;
            
            if (i == s2.length())
                return false;
            
            k++;
        }
        
        return false;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(s2<sup>2</sup>)
- Space Complexity: O(1)
