### Solution

```java
class Solution {
    
    public int [][] intervalIntersection(int [][] firstList, int [][] secondList) {
        if (firstList.length == 0 || secondList.length == 0)
            return new int [][] {};
        
        List<Integer []> ansList = new ArrayList<>();
        
        int f, s, firstLen, secondLen;
        firstLen = firstList.length;
        secondLen = secondList.length;
        
        f = 0;
        s = 0;
        while (f < firstLen && s < secondLen) {
            int firstStart = firstList[f][0];
            int secondStart = secondList[s][0];
            int firstEnd = firstList[f][1];
            int secondEnd = secondList[s][1];
            if (firstEnd < secondStart || secondEnd < firstStart) {
                if (firstEnd < secondStart)
                    f++;
                else
                    s++;
            }
            else {
                int maxEnd = Math.max(firstEnd, secondEnd);
                int minEnd = Math.min(firstEnd, secondEnd);
                int maxStart = Math.max(firstStart, secondStart);
                Integer [] ans = new Integer [] {minEnd, maxStart};
                if (ans[0] > ans[1]) {
                    int temp = ans[0];
                    ans[0] = ans[1];
                    ans[1] = temp;
                }
                ansList.add(ans);
                if (firstEnd == maxEnd)
                    s++;
                if (secondEnd == maxEnd)
                    f++;
            }
        }
        
        int [][] ansArray = new int [ansList.size()][2];
        for (int i = 0; i < ansList.size(); i++) {
            ansArray[i][0] = ansList.get(i)[0];
            ansArray[i][1] = ansList.get(i)[1];
        }
        
        return ansArray;
    }
}
```

### Time/Space Compelxity

- Time Complexity: O(m + n)
- Space Compelxity: O(m + n)
