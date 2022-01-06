### Solution

```java
class Solution {
    
    public int [] sortArrayByParity(int[] nums) {
        int left = 0, right = nums.length - 1;
        while (left <= right) {
            if (nums[left] % 2 == 0) {
                left++;
            }
            else {
                int temp = nums[right];
                nums[right] = nums[left];
                nums[left] = temp;
                right--;
            }
        }
        return nums;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
