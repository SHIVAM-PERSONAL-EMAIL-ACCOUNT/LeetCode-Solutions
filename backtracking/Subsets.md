### Solution

```java
class Solution {
    
    Deque<Integer> stack;
    List<List<Integer>> res;
    
    public List<List<Integer>> subsets(int [] nums) {
        res = new LinkedList<>();
        stack = new ArrayDeque<>();
        res.add(new LinkedList<>());
        subsets(nums, 0, nums.length);
        return res;
    }
    
    public void subsets(int [] nums, int start, int end) {
        if (start == end)
            return;
        
        while (start < end) {
            stack.push(nums[start]);
            res.add(new LinkedList<>(stack));
            subsets(nums, start + 1, end);
            stack.pop();
            start++;
        }
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n * 2<sup>n</sup>)
- Space Complexity: O(n)
