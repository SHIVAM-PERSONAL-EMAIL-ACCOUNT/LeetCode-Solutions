### Solution

```java
/*
Time Complexity: O(combinationLength * numberOfCalls)
Space Complexity: O(combinationLength)
*/
class CombinationIterator {

    String characters;
    int combinationLength;
    int size;
    int [] pointerIndices;
    
    /*
    Time Complexity: O(combinationLength)
    Space Complexity: O(combinationLength)
    */
    public CombinationIterator(String characters, int combinationLength) {
        this.characters = characters;
        this.combinationLength = combinationLength;
        this.size = characters.length();
        this.pointerIndices = new int [combinationLength];
        this.initializeArrayOfPointers();
    }
    
    /*
    Time Complexity: O(combinationLength)
    */
    public void initializeArrayOfPointers() {
        for (int i = 0; i < this.combinationLength; i++)
            pointerIndices[i] = i;
        // In order to get the first combination, we need to adjust the last pointer index otherwise it will skip one combination
        pointerIndices[combinationLength - 1]--;
    }
    
    /*
    Time Complexity: O(combinationLength)
    Space Complexity: O(combinationLength)
    */
    public String next() {
        if (pointerIndices[combinationLength - 1] != size - 1) {
            pointerIndices[combinationLength - 1]++;
            return getNext();
        }
        computeNext(1);
        return getNext();
    }
    
    /*
    Time Complexity: O(combinationLength)
    Space Complexity: O(combinationLength)
    */
    public void computeNext(int pointer) {
        int pointerIndex = pointerIndices[pointer];
        if (pointerIndex == size - combinationLength + pointer) {
            adjustPointers(pointer - 1);
            return;
        }
        computeNext(pointer + 1);
    }
    
    /*
    Time Complexity: O(combinationLength)
    */
    public void adjustPointers(int pointer) {
        pointerIndices[pointer]++;
        for (int i = pointer + 1; i < combinationLength; i++)
            pointerIndices[i] = pointerIndices[i - 1] + 1;
    }
    
    /*
    Time Complexity: O(combinationLength)
    */
    public String getNext() {
        StringBuilder res = new StringBuilder();
        for (int i = 0; i < combinationLength; i++)
            res.append(characters.charAt(pointerIndices[i]));
        return res.toString();
    }
    
    /*
    Time Complexity: O(1)
    */
    public boolean hasNext() {
        return !(pointerIndices[0] == size - combinationLength);
    }
}

/**
 * Your CombinationIterator object will be instantiated and called as such:
 * CombinationIterator obj = new CombinationIterator(characters, combinationLength);
 * String param_1 = obj.next();
 * boolean param_2 = obj.hasNext();
 */
 ```
