### Solution

```java
class Solution {
    
    List<List<Integer>> graph;
    int [] indegrees;
    int [] order;
    int orderPt;
    
    public int [] findOrder(int numCourses, int [][] prerequisites) {
        initializeGraph(numCourses, prerequisites);
        sort();
        return order;
    }
    
    public void initializeGraph(int numCourses, int [][] prerequisites) {
        graph = new ArrayList<>();
        for (int i = 0; i < numCourses; i++)
            graph.add(new LinkedList<>());
        for (int [] prerequisite : prerequisites)
            graph.get(prerequisite[1]).add(prerequisite[0]);
    }
    
    public void sort() {
        computeIndegrees();
        order = new int [graph.size()];
        orderPt = 0;
        Queue<Integer> queue = new ArrayDeque<>();
        for (int i = 0; i < indegrees.length; i++)
            if (indegrees[i] == 0)
                queue.add(i);
        while(!queue.isEmpty()) {
            Integer node = queue.poll();
            order[orderPt++] = node;
            for (Integer neighbour : graph.get(node)) {
                indegrees[neighbour]--;
                if (indegrees[neighbour] == 0)
                    queue.add(neighbour);
            }
        }
        if (orderPt != order.length)
            order = new int [0];
    }
    
    public void computeIndegrees() {
        indegrees = new int [graph.size()];
        for (List<Integer> neighbours : graph)
            for (Integer neighbour : neighbours)
                indegrees[neighbour]++;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(v + e)
- Space Complexity: O(v + e)
