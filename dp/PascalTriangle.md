### Solution

```java
class Solution {
    
    List<List<Integer>> ans;
        
    public List<List<Integer>> generate(int n) {
        ans = new ArrayList<>();
        
        ans.add(new LinkedList<>());
        ans.get(0).add(1);
        if (n == 1) return ans;
        
        ans.add(new LinkedList<>());
        ans.get(1).add(1);
        ans.get(1).add(1);
        if (n == 2) return ans;
        
        for (int i = 1; i < n - 1; i++) {
            List<Integer> list = new LinkedList<>();
            list.add(1);
            List<Integer> prev = ans.get(i);
            for (int j = 1; j < prev.size(); j++)
                list.add(prev.get(j) + prev.get(j - 1));
            list.add(1);
            ans.add(list);
        }
        
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(n<sup>2</sup>)
