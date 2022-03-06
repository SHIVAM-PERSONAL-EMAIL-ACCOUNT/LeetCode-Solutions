### Solution

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    
    public List<List<Integer>> resPaths = new ArrayList<>();
    
    public List<List<Integer>> pathSum(TreeNode root, int targetSum) {
        DFS(root, 0, targetSum, new ArrayList<>());
        return resPaths;
    }
    
    public void DFS(TreeNode node, long sum, int targetSum, List<Integer> path) {
        if (node == null) return;
        
        sum += node.val;
        path.add(node.val);
        
        if (node.left == null && node.right == null) {
            if (sum == targetSum) savePath(path); 
            path.remove(path.size() - 1);
            return;
        }
        
        DFS(node.left, sum, targetSum, path);
        DFS(node.right, sum, targetSum, path);
        
        path.remove(path.size() - 1);
    }
    
    public void savePath(List<Integer> path) {
        List<Integer> temp = new ArrayList<>();
        for (int point : path)
            temp.add(point);
        resPaths.add(temp);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
