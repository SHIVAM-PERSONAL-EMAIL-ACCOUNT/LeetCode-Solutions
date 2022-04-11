### Solution

```java
class Solution {
   
    Map<Character,Integer> map;
   
    public void initializeMap() {
        map = new HashMap<>();
        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C', 100);
        map.put('D', 500);
        map.put('M', 1000);
    }    
    
    public int romanToInt(String str) {
        initializeMap();
        int s = str.length();
        int number = 0;
        int i = s - 1;
        while (i >= 0) {
            char ch = str.charAt(i);
            number += map.get(ch);
            switch(ch) {
                case 'V':
                case 'X':
                    if (i - 1 >= 0 && str.charAt(i - 1) == 'I') {
                        number -= 1;
                        i--;
                    }
                    break;
                case 'L':
                case 'C':    
                    if (i - 1 >= 0 && str.charAt(i - 1) == 'X') {
                        number -= 10;
                        i--;
                    }
                    break;
                case 'D':
                case 'M':    
                    if (i - 1 >= 0 && str.charAt(i - 1) == 'C') {
                        number -= 100;
                        i--;
                    }
                    break;                    
            }
            i--;
        }
        return number;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
