### Solution

```java
class Solution {
    
    public List<List<String>> groupAnagrams(String [] strs) {
        Map<String,List<String>> map = new HashMap<>();
        for (String str : strs) {
            String hashCode = getHashCode(str);
            map.putIfAbsent(hashCode, new LinkedList<>());
            map.get(hashCode).add(str);
        }
        List<List<String>> res = new LinkedList<>();
        for (List<String> values : map.values())
            res.add(values);
        return res;
    }
    
    public String getHashCode(String str) {
        char [] arr = str.toCharArray();
        Arrays.sort(arr);
        return new String(arr);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(strs * (str * log(str)))
- Space Complexity: O(strs)
