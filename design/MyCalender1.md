### Solution

```java
class MyCalendar {

    TreeMap<Integer, Integer> map;
    
    public MyCalendar() {
        map = new TreeMap<>();        
    }
    
    public boolean book(int start, int end) {
        Integer startFloor = map.floorKey(start);
        Integer startCeiling = map.ceilingKey(start);
        Integer endFloor = map.floorKey(end - 1);
        Integer endCeiling = map.ceilingKey(end - 1);
        if ((startFloor != null && map.get(startFloor) >= start) || 
            (startCeiling != null && startCeiling <= (end - 1)) ||
            (endFloor != null && endFloor >= start) ||
            (endCeiling != null && endCeiling == (end - 1))
           )
            return false;
        map.put(start, end - 1);
        return true;
    }
}

/**
 * Your MyCalendar object will be instantiated and called as such:
 * MyCalendar obj = new MyCalendar();
 * boolean param_1 = obj.book(start,end);
 */
 ```
 
 ### Time/Space Complexity
 
 - Time Complexity: O(n log n) where `n` is the number of times `book` method is called
 - Space Complexity: O(n) where `n` is the number of times `book` method is called
