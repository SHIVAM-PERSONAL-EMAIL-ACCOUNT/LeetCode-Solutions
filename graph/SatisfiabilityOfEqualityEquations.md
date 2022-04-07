### Solution

```java
class Solution {
    
    int [] arr;
    int [] rank;
    
    
    public boolean equationsPossible(String [] equations) {
        arr = new int [26];
        rank = new int [26];
        
        for (int i = 0; i < 26; i++) {
            arr[i] = i;
            rank[i] = 0;
        }
        
        for (String equation : equations)
            if (equation.charAt(1) == '=')
                unionize(equation.charAt(0) - 'a', equation.charAt(3) - 'a');
        
        for (String equation : equations)
            if (equation.charAt(1) == '!')
                if (getParent(equation.charAt(0) - 'a') == getParent(equation.charAt(3) - 'a'))
                    return false;
        
        return true;
    }
    
    public void unionize(int variable1, int variable2) {
        int parent1 = getParent(variable1);
        int parent2 = getParent(variable2);
        if (rank[parent1] < rank[parent2])
            arr[parent1] = parent2;
        else if (rank[parent2] < rank[parent1])
            arr[parent2] = parent1;
        else {
            arr[parent1] = parent2;
            rank[variable2]++;
        }
    }
    
    public int getParent(int alpha) {
        if (arr[alpha] == alpha) return alpha;
        arr[alpha] = getParent(arr[alpha]);
        return arr[alpha];
    }
    
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n) 
