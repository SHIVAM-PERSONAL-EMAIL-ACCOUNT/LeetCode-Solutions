### Solution

```java
class Solution {
    
    public int[] sortArrayByParityII(int[] nums) {
        int oddC = nums.length - 1, evenC = 0;
        
        while (evenC < nums.length && oddC >= 0) {
            while (evenC < nums.length && nums[evenC] % 2 == 0)
                evenC += 2;
            
            while (oddC >= 0 && nums[oddC] % 2 == 1)
                oddC -= 2;
            
            if (evenC < nums.length && oddC >= 0) {
                int temp = nums[evenC];
                nums[evenC] = nums[oddC];
                nums[oddC] = temp;
                oddC -= 2;
                evenC += 2;
            }
        }
        
        return nums;
    }
}
```
### Time/Complexity

- Time Complexity: O(n) under the given constraints
- Space Complexity: O(1) 
