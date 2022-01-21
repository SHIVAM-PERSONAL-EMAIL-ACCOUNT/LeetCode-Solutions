### Solution

```java
class Solution {
    
    public int triangleNumber(int [] nums) {
        Arrays.sort(nums);
        
        int low, high, thirdSideLen, middle, count = 0;
        
        for(int i = nums.length - 1; i > 1; i--) {
            for (int j = i - 1; j > 0; j--) {
                low = 0;
                high = j - 1;
                thirdSideLen = nums[i] - nums[j];
                while (low <= high) {
                    middle = (low + high)/2;
                    if (nums[middle] > thirdSideLen) high = middle - 1;
                    else low = middle + 1;
                }
                count += (j - low);
            }
        }
        
        return count;
    }
}
```

### Time/Space Complexity

- Time Compelxity: O(n<sup>2</sup>log(n))
- Space Complexity: O(log(n))
