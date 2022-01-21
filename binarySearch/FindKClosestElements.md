### Solution

```java
class Solution {
    
    public List<Integer> findClosestElements(int [] arr, int k, int x) {
        int low, high, middle, curr;
        List<Integer> ans = new ArrayList<>();
        
        low = 0;
        high = arr.length - 1;
        while (low <= high) {
            middle = (low + high)/2;
            if (arr[middle] == x) break;
            else if (arr[middle] > x) high = middle - 1;
            else low = middle + 1;
        }
        
        if (low >= arr.length) low = arr.length - 1;
        
        curr = low;        
        if (curr - 1 >= 0) {
            if (Math.abs(arr[curr - 1] - x) <= Math.abs(arr[low] - x))
                low = curr - 1;
        }
        if (curr + 1 < arr.length) {
            if (Math.abs(arr[curr + 1] - x) < Math.abs(arr[low] - x))
                low = curr + 1;
        }
        
        ans.add(arr[low]);
        
        high = low + 1;
        low = low - 1;
        while (--k > 0) {
            if (low >= 0 && high < arr.length) {
                if (Math.abs(arr[low] - x) <= Math.abs(arr[high] - x)) {
                    ans.add(0, arr[low]);
                    low--;
                }
                else {
                    ans.add(arr[high]);
                    high++;
                }
            }
            else if (low >= 0) {
               ans.add(0, arr[low]);
                    low--; 
            }
            else {
                ans.add(arr[high]);
                    high++;
            }
        }
        
        return ans;
    }
}
```

### Time/Space Complexity

- Time Compelxity: O(log(n) + k)
- Space Complexity: O(1)
