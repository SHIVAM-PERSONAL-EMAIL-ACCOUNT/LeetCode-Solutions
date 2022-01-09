### Solution

```java
class Solution {
    
    public int distanceBetweenBusStops(int [] distance, int start, int destination) {
        if (start == destination) return 0;
        
        int firstWay = 0;
        int secondWay = 0;
        for (int value : distance)
            secondWay += value;
        
        if (start < destination) {
            int startIndex = start;
            int desIndex = destination - 1;
            for (int i = startIndex; i <= desIndex; i++) {
                firstWay += distance[i];
                secondWay -= distance[i];
            }
        }
        else {
            int startIndex = start - 1;
            int desIndex = destination;
            for (int i = startIndex; i >= desIndex; i--) {
                firstWay += distance[i];
                secondWay -= distance[i];
            }
        }
        
        return Math.min(firstWay, secondWay);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
