### Solution

```java
class Solution {
    
    public int largestSumAfterKNegations(int [] nums, int k) {
        Queue<Integer> posPQ = new PriorityQueue<>();
        Queue<Integer> negPQ = new PriorityQueue<>();
        
        for (int num : nums) {
            if (num < 0)
                negPQ.add(num);
            else
                posPQ.add(num);
        }
        
        while (!negPQ.isEmpty() && k != 0) {
            posPQ.add(negPQ.poll() * (-1));
            --k;
        }
        
        while (!negPQ.isEmpty())
            posPQ.add(negPQ.poll());
        
        int sum = 0;
        
        sum += posPQ.poll() * (int) Math.pow(-1, k);
        while(!posPQ.isEmpty())
            sum += posPQ.poll();
        
        return sum; 
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(n)
