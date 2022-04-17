### Solution

```java
class Solution {
    
    Map<Character,Integer> map;
    
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        
        map = new HashMap<>();
        
        for (char ch : s.toCharArray())
            map.put(ch, map.getOrDefault(ch,0) + 1);
        
        for (char ch : t.toCharArray())
            if (!map.containsKey(ch) || map.get(ch) == 0)
                return false;
            else 
                map.put(ch, map.get(ch) - 1);
                
        return true;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(s + t)
- Space Complexity: O(s)
