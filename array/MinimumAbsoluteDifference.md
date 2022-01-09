### Solution

```java
class Solution {
    
    public List<List<Integer>> minimumAbsDifference(int [] arr) {
        Arrays.sort(arr);
        
        int minDiff = Integer.MAX_VALUE;
        for (int i = 1; i < arr.length; i++)
            if (arr[i] - arr[i - 1] < minDiff)
                minDiff = arr[i] - arr[i - 1];
        
        List<List<Integer>> list = new ArrayList<>();
        
        for (int i = 1; i < arr.length; i++)
            if (arr[i] - arr[i - 1] == minDiff)
                list.add(Arrays.asList(arr[i - 1], arr[i]));
        
        return list;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(1)
