### Solution

```java
class Solution {

    public int [] fairCandySwap(int [] aliceSizes, int [] bobSizes) {
        int bobSum = 0, aliceSum = 0;
        for (int bob : bobSizes)
            bobSum += bob;
        for (int alice : aliceSizes)
            aliceSum += alice;
        
        int exchangeBoxDiff = Math.abs(bobSum - aliceSum)/2;
        int [] answers = new int [2];
        
        if (bobSum > aliceSum) {
            HashSet<Integer> aliceSet = new HashSet<>();
            for (int alice : aliceSizes) 
                aliceSet.add(alice);
            
            for (int bob : bobSizes) {
                if (aliceSet.contains(bob - exchangeBoxDiff)) {
                    answers[0] = bob - exchangeBoxDiff;
                    answers[1] = bob;
                    return answers;
                 }
            }
        }
        else {
            HashSet<Integer> bobSet = new HashSet<>();
            for (int bob : bobSizes) 
                bobSet.add(bob);
            
            for (int alice : aliceSizes) {
                if (bobSet.contains(alice - exchangeBoxDiff)) {
                    answers[0] = alice;
                    answers[1] = alice - exchangeBoxDiff;
                    return answers;
                }
            }
        }
        
        return answers;
    }
}
```
