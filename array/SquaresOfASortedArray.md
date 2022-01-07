### Solution

```java
class Solution {
    
    public int [] sortedSquares(int [] nums) {
        Deque<Integer> stack = new LinkedList<>();
        Deque<Integer> queue = new LinkedList<>();
        
        for (int num : nums) {
            if (num >= 0)
                stack.push(num * num);
            else
                queue.add(num * num);
        }
        
        int i = nums.length - 1;
        while (!stack.isEmpty() || !queue.isEmpty()) {
            if (stack.isEmpty())
                nums[i--] = queue.poll();
            else if (queue.isEmpty())
                nums[i--] = stack.pop();
            else {
                if (stack.peek() > queue.peek())
                    nums[i--] = stack.pop();
                else
                    nums[i--] = queue.poll();
            }
        }
        
        return nums;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
