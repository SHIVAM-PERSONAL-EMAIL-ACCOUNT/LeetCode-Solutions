### Solution

```java
class Solution {
    
    public List<String> findRepeatedDnaSequences(String s) {
        if (s.length() < 10)
            return new ArrayList<String>();
        
        List<String> ans = new ArrayList<>();
        Map<String, Integer> sequence = new HashMap<>();
        int size, i;
        String str;

        str = s.substring(0, 10);
        sequence.put(str, 1);
        size = s.length();
        for (i = 10; i < size; i++) {
            str = str.substring(1, 10) + s.charAt(i); 
            sequence.put(str, sequence.getOrDefault(str, 0) + 1);
        }
        
        for (String key : sequence.keySet()) {
            if (sequence.get(key) > 1)
                ans.add(key.toString());
        }
        
        return ans;
    }
}
```
### Time/Space Compelxity

- Time Compelxity: O(n)
- Space Compelxity: O(n)
