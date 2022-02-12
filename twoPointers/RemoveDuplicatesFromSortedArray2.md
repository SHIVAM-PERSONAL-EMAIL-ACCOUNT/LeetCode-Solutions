### Solution

```java
class Solution {
    
    public int removeDuplicates(int [] nums) {
        int i = 0, k = 0, n = nums.length;
        while (i < n) {
            int curr = nums[i], count = 1;
            while (i < n && nums[i] == curr) {
                if (count <= 2)
                    nums[k++] = curr;
                count++;
                i++;
            }
        }
        return k;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Compleixty: O(1)
