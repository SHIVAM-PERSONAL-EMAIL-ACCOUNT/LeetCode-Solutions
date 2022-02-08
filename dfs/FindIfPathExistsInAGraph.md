### Solution

```java
class Solution {
    
    public boolean validPath(int n, int [][] edges, int source, int destination) {
        if (edges.length == 0) return true;
        Map<Integer, List<Integer>> graph = constructGraph(edges);
        int [] visited = new int [n];
        return checkPath(visited, graph, source, destination);
    }
    
    public boolean checkPath(int [] visited, Map<Integer, List<Integer>> graph, int source, int destination) {
        boolean exists = false;
        visited[source] = 1;
        if (!graph.containsKey(source)) return false;
        List<Integer> neighbours = graph.get(source);
        for (Integer neighbour : neighbours) {
            if (neighbour == destination) return true;
            if (visited[neighbour] != 1) exists = checkPath(visited, graph, neighbour, destination);
            if (exists) break;
        }
        return exists;
    }
    
    public Map<Integer, List<Integer>> constructGraph(int [][] edges) {
        Map<Integer, List<Integer>> map = new HashMap<>();
        for (int [] edge : edges) {
            if (map.containsKey(edge[0])) {
                map.get(edge[0]).add(edge[1]);
            }
            else {
                List<Integer> neighbours = new ArrayList<>();
                neighbours.add(edge[1]);
                map.put(edge[0], neighbours);
            }
            if (map.containsKey(edge[1])) {
                map.get(edge[1]).add(edge[0]);
            }
            else {
                List<Integer> neighbours = new ArrayList<>();
                neighbours.add(edge[0]);
                map.put(edge[1], neighbours);
            }
        }
        return map;
    }
}
```

### Time/Space Compelxity

- Time Compelxity: O(n<sup>2</sup>), `n` is the number of vertices in the graph
- Space Complexity: O(n<sup>2</sup>)
