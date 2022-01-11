### Solution

```java
class Solution {
    
    public boolean checkIfExist(int [] arr) {
        Set<Integer> set = new HashSet<>();
        int countOf0 = 0;
        for (int num : arr) {
            set.add(num*2);
            if (num == 0)
                countOf0++;
        }
        if (countOf0 > 1) return true;
        for (int num : arr)
            if (set.contains(num) && num != 0)
                return true;
        return false;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n) 
- Space Complexity: O(n)
