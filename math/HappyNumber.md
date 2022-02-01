### Solution

```java
class Solution {
    
    public boolean isHappy(int n) {
        Set<Long> set = new HashSet<>();
        long num = n;
        while (num != 1) {
            num = sumOfDigits(num);
            if (set.contains(num)) return false;
            else set.add(num);
        }
        return true;
    }
    
    public long sumOfDigits(long num) {
        long sum = 0;
        while (num != 0) {
            int digit = (int)(num % 10);
            sum += digit*digit;
            num /= 10;
        }
        return sum;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(log n)
- Space Complexity: O(log n)
