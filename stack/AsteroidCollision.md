### Solution

```java
class Solution {
    
    public int [] asteroidCollision(int [] asteroids) {
        List<Integer> ansList = new ArrayList<>();
        Deque<Integer> rightArmy = new ArrayDeque<>();
        for (int asteroid : asteroids) {
            if (asteroid > 0) rightArmy.push(asteroid);
            else {
                int leftWarrior = -asteroid;
                while (!rightArmy.isEmpty()) {
                    if (leftWarrior == rightArmy.peek()) { rightArmy.pop(); leftWarrior = 0; break; }
                    else if ((leftWarrior < rightArmy.peek())) { leftWarrior = 0; break; }
                    else rightArmy.pop();
                }
                if (rightArmy.isEmpty() && leftWarrior != 0) ansList.add(-leftWarrior);
            }
        }
        while (!rightArmy.isEmpty())
            ansList.add(rightArmy.pollLast());
        return getAnsArray(ansList);
        
    }
    
    public int [] getAnsArray(List<Integer> ansList) {
        int [] ansArray = new int [ansList.size()];
        for (int i = 0; i < ansList.size(); i++)
            ansArray[i] = ansList.get(i);
        return ansArray;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Compelxity: O(n)
