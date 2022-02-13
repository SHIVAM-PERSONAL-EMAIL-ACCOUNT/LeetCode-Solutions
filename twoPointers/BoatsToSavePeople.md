### Solution

```java
class Solution {
    
    public int numRescueBoats(int [] people, int limit) {
        if (people.length == 1)
            return 1;
        
        int i, j, count, peoples;
        peoples = people.length;
        
        Arrays.sort(people);
        
        count = 0;
        i = 0;
        j = peoples - 1;
        while (i < j) {
            if (people[i] + people[j] <= limit)
                i++;
            ++count;
            j--;
        }
        
        if (i == j) 
            ++count;
        
        return count;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Compleixty: O(log n)
