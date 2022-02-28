### Solution

```java
class Solution {
    
    public int [] nextGreaterElements(int [] nums) {
        int len = nums.length;
        int [] temp = new int [2 * len];
        int [] ans = new int [2 * len];
        Deque<Integer> stack = new ArrayDeque<>();
        int k = 0;
        
        for (int i = 0; i < 2; i++)
            for (int j = 0; j < len; j++)
                temp[k++] = nums[j];
        
        k = 2 * len - 1;
        while (k >= 0) {
            while (!stack.isEmpty() && stack.peek() <= temp[k])
                stack.pop();
            if (stack.isEmpty()) ans[k] = -1;
            else ans[k] = stack.peek();
            stack.push(temp[k]);
            k--;
        }
        
        int [] finalAns = new int [len];
        for (int i = 0; i < len; i++)
            finalAns[i] = ans[i];
        
        return finalAns;
    }
}
```

### Time/Space Complexity

- Time Compelxity: O(n)
- Space Complexity: O(n)
