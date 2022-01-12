### Solution

```java
class Solution {
    
    public List<List<Integer>> threeSum(int [] nums) {
        Set<List<Integer>> set = new HashSet<>();
        List<List<Integer>> ans = new ArrayList<>();
        Arrays.sort(nums);
        for (int i = 0; i < nums.length - 2; i++) {
            int leftPt = i + 1, rightPt = nums.length - 1, sum;
            while (leftPt < rightPt) {
                sum = nums[i] + nums[leftPt] + nums[rightPt];
                if (sum == 0) { set.add(new ArrayList(Arrays.asList(nums[i], nums[leftPt], nums[rightPt]))); leftPt++; }
                else if (sum > 0) rightPt--;
                else leftPt++;
            }
        }
        for (List<Integer> list : set)
            ans.add(list);
        return ans;
   ```
   
   ### Time/Space Complexity
   
   - Time Complexity: O(n<sup>2</sup>)
   - Space Complexity: O(n)
