### Solution

```java
class Solution {
    
    public int maxSatisfied(int [] customers, int [] grumpy, int minutes) {
        List<Integer> grumpyIndices = new ArrayList<>();
        int limit = customers.length;
        int satisfiedCustomers = 0;
        
        for (int i = 0; i < limit; i++)
            if (grumpy[i] == 0) satisfiedCustomers += customers[i];
            else grumpyIndices.add(i);
        
        int maxSatisfiedCustomers = 0;
        int potentiallySatisfiedCustomers = 0;
        int right = 0;
        int left = 0;
        while (right < grumpyIndices.size()) {
            potentiallySatisfiedCustomers += customers[grumpyIndices.get(right)];
            while (grumpyIndices.get(left) < grumpyIndices.get(right) && 
                   grumpyIndices.get(right) - grumpyIndices.get(left) + 1 > minutes)
                potentiallySatisfiedCustomers -= customers[grumpyIndices.get(left++)];
            maxSatisfiedCustomers = Math.max(maxSatisfiedCustomers, potentiallySatisfiedCustomers);
            right++;
        }
        
        return satisfiedCustomers + maxSatisfiedCustomers;
    }
}
```

### Timne/Space Compelxity

- Time Complexity: O(n)
- Space Compelxity: O(n)
