### Solution

```java
class Solution {
    
    public String pushDominoes(String dominoes) {
        int i, d, nearestRightFallingDomino, nearestLeftFallingDomino;
        d = dominoes.length();
        
        int [] distanceFromNearestRight = new int [d];
        int [] distanceFromNearestLeft = new int [d];
        
        nearestRightFallingDomino = d + 1;
        for (i = 0; i < d; i++) {
            char domino = dominoes.charAt(i);
            if (domino == '.') {
                distanceFromNearestRight[i] = nearestRightFallingDomino++;
            }
            else {
                if (domino == 'R')
                    nearestRightFallingDomino = 1;
                else
                    nearestRightFallingDomino = d + 1;
                distanceFromNearestRight[i] = -1;
            }
        }
        
        nearestLeftFallingDomino = d + 1;
        for (i = d - 1; i >= 0; i--) {
            char domino = dominoes.charAt(i);
            if (domino == '.') {
                distanceFromNearestLeft[i] = nearestLeftFallingDomino++;
            }
            else {
                if (domino == 'L')
                    nearestLeftFallingDomino = 1;
                else
                    nearestLeftFallingDomino = d + 1;
                distanceFromNearestLeft[i] = -1;
            }
        }
        
        StringBuilder res = new StringBuilder();
        
        for (i = 0; i < d; i++) {
            if (distanceFromNearestRight[i] == -1)
                res.append(dominoes.charAt(i));
            else if (distanceFromNearestRight[i] >= d + 1 && distanceFromNearestLeft[i] >= d + 1)
                res.append(".");
            else
                if (distanceFromNearestRight[i] > distanceFromNearestLeft[i]) res.append("L");
                else if (distanceFromNearestRight[i] < distanceFromNearestLeft[i]) res.append("R");
                else res.append(".");
        }
        
        return res.toString();
    }
}
```

### Time/Space Complexity

- Time Compelxity: O(n)
- Space Compelxity: O(n)
