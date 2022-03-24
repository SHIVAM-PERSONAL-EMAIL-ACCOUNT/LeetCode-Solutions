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
    Map<Integer, Integer> pointerIndices;
    
    /*
    Time Complexity: O(combinationLength)
    Space Complexity: O(combinationLength)
    */
    public CombinationIterator(String characters, int combinationLength) {
        this.characters = characters;
        this.combinationLength = combinationLength;
        this.size = characters.length();
        this.pointerIndices = new HashMap<>();
        this.initializeMapOfPointers();
    }
    
    /*
    Time Complexity: O(combinationLength)
    */
    public void initializeMapOfPointers() {
        for (int i = 0; i < this.combinationLength; i++)
            pointerIndices.put(i + 1, i);
        // In order to get the first combination, we need to adjust the last pointer index otherwise it will skip one combination
        pointerIndices.put(this.combinationLength, pointerIndices.get(this.combinationLength) - 1);
    }
    
    /*
    Time Complexity: O(combinationLength)
    Space Complexity: O(combinationLength)
    */
    public String next() {
        if (pointerIndices.get(combinationLength) != size - 1) {
            pointerIndices.put(combinationLength, pointerIndices.get(combinationLength) + 1);
            return getNext();
        }
        computeNext(2);
        return getNext();
    }
    
    /*
    Time Complexity: O(combinationLength)
    Space Complexity: O(combinationLength)
    */
    public void computeNext(int pointer) {
        int pointerIndex = pointerIndices.get(pointer);
        if (pointerIndex == size - combinationLength + (pointer - 1)) {
            adjustPointers(pointer - 1);
            return;
        }
        computeNext(pointer + 1);
    }
    
    /*
    Time Complexity: O(combinationLength)
    */
    public void adjustPointers(int pointer) {
        pointerIndices.put(pointer, pointerIndices.get(pointer) + 1);
        for (int i = pointer + 1; i <= combinationLength; i++)
            pointerIndices.put(i, pointerIndices.get(i - 1) + 1);
    }
    
    /*
    Time Complexity: O(combinationLength)
    */
    public String getNext() {
        StringBuilder res = new StringBuilder();
        for (int i = 0; i < combinationLength; i++)
            res.append(characters.charAt(pointerIndices.get(i + 1)));
        return res.toString();
    }
    
    /*
    Time Complexity: O(1)
    */
    public boolean hasNext() {
        return !(pointerIndices.get(1) == size - combinationLength);
    }
}

/**
 * Your CombinationIterator object will be instantiated and called as such:
 * CombinationIterator obj = new CombinationIterator(characters, combinationLength);
 * String param_1 = obj.next();
 * boolean param_2 = obj.hasNext();
 */
 ```
