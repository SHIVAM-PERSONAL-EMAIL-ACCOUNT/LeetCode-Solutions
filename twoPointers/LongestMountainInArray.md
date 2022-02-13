### Solution

```java
class Solution {
    
    public int longestMountain(int [] nums) {
        int i = 0, size, ans = 0; 
        size = nums.length;
        
        while (i + 1 < size) {
            if (nums[i] < nums[i + 1]) {
                int start = i;
                int curr = i + 1;
                while (curr + 1 < size && nums[curr] < nums[curr + 1])
                    curr++;
                if (curr + 1 == size || nums[curr] == nums[curr + 1]) {
                    i = curr + 1;    
                }
                else {
                    while (curr + 1 < size && nums[curr + 1] < nums[curr])
                        curr++;
                    ans = Math.max(ans, curr - start + 1);
                    i = curr;
                }
            }
            else {
                i++;
            }
        }
        
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Compelxity: O(1)
