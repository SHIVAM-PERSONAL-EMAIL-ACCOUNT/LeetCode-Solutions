### Solution

```java
class Solution {
    
    List<List<Integer>> graph;
    Set<Integer> cycleFreeCourses;
    Set<Integer> underInvestigationCourses;
    
    public boolean canFinish(int numCourses, int [][] prerequisites) {
        initializeGraphOfPrerequisites(numCourses, prerequisites);
        return !hasCircularDependencyInGraph(numCourses);
    }
    
    public void initializeGraphOfPrerequisites(int numCourses, int [][] prerequisites) {
        graph = new ArrayList<>();
        
        for (int i = 0; i < numCourses; i++)
            graph.add(new ArrayList<>());
        
        for (int [] pair : prerequisites) {
            int dependentCourse = pair[0];
            int dependentOn = pair[1];
            graph.get(dependentCourse).add(dependentOn);
        }
    }
    
    public boolean hasCircularDependencyInGraph(int numCourses) {
        cycleFreeCourses = new HashSet<>();
        underInvestigationCourses = new HashSet<>();
        for (int i = 0; i < numCourses; i++)
            if (hasCycle(i))
                return true;
        return false;
    }
    
    public boolean hasCycle(int currCourse) {
        if (cycleFreeCourses.contains(currCourse))
            return false;
        
        if (underInvestigationCourses.contains(currCourse))
            return true;
        
        underInvestigationCourses.add(currCourse);
        
        List<Integer> dependencies = graph.get(currCourse);
        for (Integer dependency : dependencies)
            if (hasCycle(dependency))
                return true;
        
        underInvestigationCourses.remove(currCourse);
        cycleFreeCourses.add(currCourse);
        return false;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(numCourses + prerequisites.length)
- Space Complexity: O(numCourses<sup>2</sup>), for construction the graph (for the extreme case where each course is dependent on every other course)
