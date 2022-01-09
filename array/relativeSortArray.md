### Solution

```java
class Solution {
    
    public class MyComparator implements Comparator<Integer> {

        Map<Integer, Integer> map = new HashMap<>();

        public MyComparator(Map<Integer, Integer> map) {
            this.map = map;
        }

        @Override
        public int compare(Integer o1, Integer o2) {
            return map.get(o1) - map.get(o2);
        } 
        
    }

    public int [] relativeSortArray(int [] arr1, int [] arr2) {
        Map<Integer, Integer> map = new HashMap<>();
        int i = 1;
        for (int num : arr2)
            map.put(num, i++);  

        Queue<Integer> queue1 = new PriorityQueue<>(new MyComparator(map));
        Queue<Integer> queue2 = new PriorityQueue<>();

        for (int num : arr1)
            if (map.containsKey(num))
                queue1.add(num);
            else
                queue2.add(num);

        i = 0;
        while(!queue1.isEmpty())
            arr1[i++] = queue1.poll();
        while(!queue2.isEmpty())
            arr1[i++] = queue2.poll();

        return arr1;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n log n)
- Space Complexity: O(n)
