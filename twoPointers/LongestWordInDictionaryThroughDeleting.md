### Solution

```java
class Solution {
    public String findLongestWord(String string, List<String> dictionary) {
        String res = "";
        int i, j, w, s;
        s = string.length();
        for (String word : dictionary) {
            i = 0; 
            j = 0;
            StringBuilder possibleAns = new StringBuilder();
            w = word.length();
            while (i < w) {
                char ch = word.charAt(i);
                while (j < s && ch != string.charAt(j))
                    j++;
                if (j == s)
                    break;
                possibleAns.append(ch);
                j++;
                i++;
            }
            if (i == w) {
                String temp = possibleAns.toString();
                if (temp.length() > res.length())
                    res = temp;
                else if (temp.length() == res.length())
                    if (res.compareTo(temp) > 0)
                        res = temp;
            }
        }
        return res;
    }
}
```

### Time/Space Complexity

#### Assumption:

For complexity analysis, the length of the `dictionary`, length of each word in dictionary and length of String `string` is considered as `n` 

- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(n)
