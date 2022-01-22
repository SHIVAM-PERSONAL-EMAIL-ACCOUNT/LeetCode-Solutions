### Solution

```java
class TimeMap {

    public class TimeValue {
        public List<Integer> timeStamps = new ArrayList<>();
        public List<String> values = new ArrayList<>();
        
        public TimeValue(List<Integer> timeStamps, List<String> values) {
            this.timeStamps = timeStamps;
            this.values = values;
        }
    }
    
    public Map<String, TimeValue> map;
    
    public TimeMap() {
        map = new HashMap<>(); 
    }
    
    public void set(String key, String value, int timeStamp) {
        TimeValue temp = map.get(key);
        if (temp == null) {
            map.put(key, new TimeValue(new ArrayList(Arrays.asList(timeStamp)), new ArrayList(Arrays.asList(value))));
        }
        else {
            temp.timeStamps.add(timeStamp);
            temp.values.add(value);
            map.put(key, temp);
        }
    }
    
    public String get(String key, int timeStamp) {
        TimeValue temp = map.get(key);
        if (temp == null || temp.timeStamps.get(0) > timeStamp) return "";
        List<Integer> timeStamps = temp.timeStamps;
        int low = 0, high = timeStamps.size() - 1;
        while (low <= high) {
            int middle = (low + high)/2;
            if (timeStamps.get(middle) == timeStamp) 
                return temp.values.get(middle);
            else if (timeStamps.get(middle) > timeStamp) 
                high = middle - 1;
            else {
                if (middle + 1 <  timeStamps.size() && timeStamps.get(middle + 1) > timeStamp)
                    return temp.values.get(middle);
                low = middle + 1;
            }
        }
        if (low > timeStamps.size() - 1) return temp.values.get(timeStamps.size() - 1);
        else return temp.values.get(low);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(log(t)), where `t` is the length of the timeStamps list
- Space Complexity: O(1); No extra space used other than the data stucture in which the data was stored
