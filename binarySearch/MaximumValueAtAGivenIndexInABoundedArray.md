### Solution

```java
class Solution {
    
    public int maxValue(int n, int index, int maxSum) {
        int min = 1, max = maxSum, ans = min;
        while (min <= max) {
            int middle = min + (max - min)/2;
            if (valueIsPossible(middle, n, index, maxSum)) { ans = middle; min = middle + 1; }
            else max = middle - 1;
        }
        return ans;
    }
    
    public boolean valueIsPossible(int value, int n, int index, int maxSum) {
        if (value == 1)
            if (n <= maxSum) return true;
            else return false;
        int sum = value, i = index, j = index, val = value;
        while (--i >= 0) {
            if (--val == 1) break;
            sum += val;
            if (sum > maxSum) return false;
        }
        sum += i + 1;
        if (sum > maxSum) return false;
        while (++j < n) {
            if (--value == 1) break;
            sum += value;
            if (sum > maxSum) return false;
        }
        sum += (n - j);
        if (sum > maxSum) return false;
        return true;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n * log(maxSum))
- Space Complexity: O(1)
