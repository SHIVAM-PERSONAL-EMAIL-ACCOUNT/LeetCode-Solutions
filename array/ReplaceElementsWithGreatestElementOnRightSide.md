### Solution

```java
class Solution {
    
    public int [] replaceElements(int [] arr) {
        int [] ans = new int [arr.length];
        ans[arr.length - 1] = -1;
        int currMax = arr[arr.length - 1];
        for (int i = arr.length - 2; i >= 0; i--) {
            ans[i] = currMax;
            if (arr[i] > currMax)
                currMax = arr[i];
        }
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
