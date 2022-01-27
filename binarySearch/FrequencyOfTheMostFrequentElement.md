### Solution

```java
class Solution {

    public int maxFrequency(int [] nums, int k) {
        Arrays.sort(nums);
        
        int right = nums.length - 1, maxLen = 1; 
        
        while (right >= 0) {
            if (right + 1 <= maxLen)
                break;
            
            int ans = -1;
                
            int start = 0, finish = right - 1;
            while (start <= finish) {
                int middle = (start + finish)/2;
                if (nums[middle] == nums[right]) 
                    finish = middle - 1;
                else {
                    ans = middle;
                    start = middle + 1;
                }
            }
            
            int len = right - ans;
            
            int i = ans, count = 0, budget = 0;
            while (i >= 0 && budget < k) {
                budget += (nums[right] - nums[i]);
                if (budget <= k) count++;
                i--;
            }
            
            len += count;
            
            maxLen = Math.max(maxLen, len);
            
            if (ans == -1)
                break;
            
            right = ans;
        }
        
        return maxLen;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(log n)
