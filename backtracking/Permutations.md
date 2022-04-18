### Solution

```java
class Solution {
    
    Set<Integer> set;
    List<Integer> list;
    List<List<Integer>> res;
    
    public List<List<Integer>> permute(int [] nums) {
        set = new HashSet<>();
        list = new ArrayList<>();
        res = new LinkedList<>();
        permute(nums, nums.length);
        return res;
    }
    
    public void permute(int [] nums, int size) {
        if (set.size() == size) {
            res.add(new LinkedList<>(list));
            return;
        }
        
        for (int num : nums) {
            if (set.add(num)) {
                list.add(num);
                permute(nums, size);
                set.remove(num);
                list.remove(list.size() - 1);
            }
        }
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n * n!)
- Space Complexity: O(n)
