### Solution

```java
class Solution {
    
    public int countStudents(int [] students, int [] sandwiches) {
        Deque<Integer> queue = new ArrayDeque<>();
        for (int student : students)
            queue.add(student);
        return getStudents(students, sandwiches, 0, queue);
    }
    
    public int getStudents(int [] students, int [] sandwiches, int top, Deque<Integer> queue) {
        int size = queue.size(), flag = 0;
        while (!queue.isEmpty() && flag++ < size) {
            Integer front = queue.poll();
            if (front == sandwiches[top]) {
                top++;
                size = queue.size();
                flag = 0;
            }
            else queue.add(front);
        }
        return queue.size();
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
