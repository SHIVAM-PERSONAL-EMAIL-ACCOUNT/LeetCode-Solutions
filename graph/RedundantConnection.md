### Solution

```java
class Solution {
    
    int [] parent;
    
    public int [] findRedundantConnection(int [][] edges) {
        parent = new int [edges.length];
        Arrays.fill(parent, -1);
        for (int [] edge : edges) {
            int parent0 = getParent(edge[0] - 1);
            int parent1 = getParent(edge[1] - 1);
            if (parent0 == parent1) return edge;
            unionize(edge[0] - 1, edge[1] - 1);
        }
        return null;
    }
    
    public int getParent(int vertex) {
        if (parent[vertex] < 0) return vertex;
        parent[vertex] = getParent(parent[vertex]);
        return parent[vertex];
    }
    
    public void unionize(int vertex0, int vertex1) {
        int parent0 = getParent(vertex0);
        int parent1 = getParent(vertex1);
        int children0 = parent[parent0];
        int children1 = parent[parent1];
        if (children0 > children1) {
            parent[parent1] = children0 + children1;
            parent[parent0] = parent1;
        }
        else {
            parent[parent0] = children0 + children1;
            parent[parent1] = parent0;
        }
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n) ammortized
- Space Complexity: O(n)
