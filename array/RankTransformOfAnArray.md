### Solution

```java
class Solution {
    
    public int [] arrayRankTransform(int [] arr) {
        if (arr.length == 0) return new int [0];
        
        int [] ans = new int [arr.length];
        Map<Integer, Integer> map = new HashMap<>();
        
        int i = 0;
        for (int num : arr)
            ans[i++] = num;
        
        Arrays.sort(ans);
        
        i = 1;
        for (int num : ans)
            if (!map.containsKey(num))
                map.put(num, i++);
            
        for (i = 0; i < ans.length; i++)
            ans[i] = map.get(arr[i]);
        
        return ans;
        
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Compelxity: O(n)
