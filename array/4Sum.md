### Solution

```java
class Solution {
    
    public List<List<Integer>> fourSum(int [] nums, int target) {
        Set<List<Integer>> set = new HashSet<>();
        List<List<Integer>> ans = new ArrayList<>();
        
        if (nums.length < 4) return ans;
        
        int left, right, sum;
        Arrays.sort(nums);
        for (int i = 0; i < nums.length - 3; i++) {
            for (int j = i + 1; j < nums.length - 2; j++) {
                left = j + 1;
                right = nums.length - 1;
                while (left < right) {
                    sum = nums[i] + nums[j] + nums[left] + nums[right];
                    if (sum == target) {
                        set.add(new ArrayList(Arrays.asList(nums[i], nums[j], nums[left], nums[right])));
                        left++;
                    }
                    else if (sum < target) left++;
                    else right--;
                }
            }
        }
        
        for (List<Integer> list : set)
            ans.add(list);
        return ans;
    }
}
```

### Time/Space Complexity:

- Time Complexity: O(n<sup>3</sup>)
- Space Complxeity: O(n)
