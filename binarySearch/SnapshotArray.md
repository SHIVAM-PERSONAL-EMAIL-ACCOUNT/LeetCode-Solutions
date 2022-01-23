### Solution

```java
class SnapshotArray {

    public TreeMap<Integer, Integer> [] snapMapArray;
    public int latestSnapId;
    
    public SnapshotArray(int length) {
        snapMapArray = new TreeMap [length];
        for (int i = 0; i < length; i++) {
            snapMapArray[i] = new TreeMap<>();
            snapMapArray[i].put(0, 0);
        }
        latestSnapId = 0;
    }
    
    public void set(int index, int val) {
        snapMapArray[index].put(latestSnapId, val);
    }
    
    public int snap() {
        return latestSnapId++;
    }
    
    public int get(int index, int snap_id) {
        return snapMapArray[index].get(snapMapArray[index].floorKey(snap_id));
    }
}

/**
 * Your SnapshotArray object will be instantiated and called as such:
 * SnapshotArray obj = new SnapshotArray(length);
 * obj.set(index,val);
 * int param_2 = obj.snap();
 * int param_3 = obj.get(index,snap_id);
 */
```

### Time/Space Complexity:

- Time Complexity: O(log(snap_id))
- Space Complexity: O(1)
