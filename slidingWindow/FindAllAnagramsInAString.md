### Solution

```java
class Solution {
    
    public List<Integer> findAnagrams(String toSearch, String toFind) {
        List<Integer> ansList = new ArrayList<>();
        int [] toSearchMap = new int [26];
        int [] toFindMap = new int [26];
        
        for (char alpha : toFind.toCharArray())
            toFindMap[alpha - 'a']++;
        
        for (int i = 0; i < 26; i++)
            toSearchMap[i] = (toFindMap[i] == 0) ? -5 : toFindMap[i];
        
        int toSearchSize = toSearch.length();
        int left = 0;
        int right = 0;
        while (right < toSearchSize) {
            char alpha = toSearch.charAt(right);
            if (toSearchMap[alpha - 'a'] == -5) {
                for (int i = 0; i < 26; i++)
                toSearchMap[i] = (toFindMap[i] == 0) ? -5 : toFindMap[i];
                left = right + 1;
                right = right + 1;
                continue;
            }
            toSearchMap[alpha - 'a']--;
            if (toSearchMap[alpha - 'a'] < 0) {
                while (toSearch.charAt(left) != alpha) {
                    toSearchMap[toSearch.charAt(left) - 'a']++;
                    left++;
                }
                toSearchMap[toSearch.charAt(left) - 'a']++;
                left++;
            }
            if (isZero(toSearchMap))
                ansList.add(left);
            right++;
        }
        
        return ansList;
    }
    
    public boolean isZero(int [] toSearchMap) {
        for (int freq : toSearchMap)
            if (freq != -5 && freq != 0)
                return false;
        return true;
    }
}
```

### Time/Space Compelxity

- Time Compelxity: O(n)
- Space Compelxity: O(1)
