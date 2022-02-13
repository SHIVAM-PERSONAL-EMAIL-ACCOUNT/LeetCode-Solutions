### Solution

```java
class Solution {
    
    public int findUnsortedSubarray(int [] nums) {
        int i, j, min, max, start, end;
        int n = nums.length;
        
        // find the first index from the beginning where the dip occurs
        i = 0;
        while (i < n - 1 && nums[i] <= nums[i + 1])
            i++;
        
        // if no dip, then array is sorted
        if (i == n - 1) 
            return 0;
        
        // find the first index from the last where the rise occurs
        j = n - 1;
        while (j > 0 && nums[j] >= nums[j - 1])
            j--;
        
        // within the found range, find the minimum and maximum number
        min = nums[i]; 
        max = nums[j];
        for (int k = i; k <= j; k++) {
            if (nums[k] < min)
                min = nums[k];
            if (nums[k] > max)
                max = nums[k];
        }
        
        // find the first number from the start which is more than the min number
        start = 0;
        while (start < n && nums[start] <= min)
            start++;
        
        // find the first number from the end which is less than the max number
        end = n - 1;
        while (end >= 0 && max <= nums[end]) {
            end--;
        }
        
        return end - start + 1;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Compelxity: O(1)
