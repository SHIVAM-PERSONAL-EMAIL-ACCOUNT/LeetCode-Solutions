### Solution

```java
class Solution {
    
    public int smallestDivisor(int [] nums, int threshold) {
        Arrays.sort(nums);
        int min = 1, max = nums[nums.length - 1];
        while (min < max) {
            int middle = min + (max - min)/2, sum = 0;
            for (int num : nums) {
                sum += num/middle;
                if (num % middle != 0) sum++;
                if (sum > threshold) break;
            }
            if (sum > threshold) min = middle + 1;
            else max = middle;
        }
        return min;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(log n)
