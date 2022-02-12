### Solution

```java
class Solution {
    
    public void sortColors(int [] nums) {
        int i = 0, j = 0;
        for (int obj = 0; obj < 2; obj++) {
            i = j;
            while (i < nums.length) {
                if (nums[i] != obj) {
                    ++i;
                    continue;
                }
                else {
                    while (j < i && nums[j] == obj) {
                        ++j;
                    }
                    if (j != i) {
                        int temp = nums[i];
                        nums[i] = nums[j];
                        nums[j] = temp;
                        ++j;
                    }
                    ++i;
                }
            }
            while (j < nums.length && nums[j] == obj) {
                ++j;
            }
        }
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
