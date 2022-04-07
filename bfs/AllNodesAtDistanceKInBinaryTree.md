### Solution

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    
    Map<TreeNode, TreeNode> map;
    List<Integer> res;
    Set<TreeNode> visited;
    
    public List<Integer> distanceK(TreeNode root, TreeNode target, int k) {
        map = new HashMap<>();
        assignParents(root, null);
        res = new LinkedList<>();
        traverseParents(target, k);
        return res;
    }
    
    public void assignParents(TreeNode child, TreeNode parent) {
        if (child == null) 
            return;
        map.put(child, parent);
        assignParents(child.left, child);
        assignParents(child.right, child);
    }
    
    public void traverseParents(TreeNode target, int k) {
        visited = new HashSet<>();
        TreeNode curr = target;
        while(curr != null && k >= 0) {
            getNodes(curr, k);
            visited.add(curr);
            curr = map.get(curr);
            k--;
        }
    }
    
    public void getNodes(TreeNode node, int k) {
        if (node == null || visited.contains(node)) 
            return;
        if (k == 0) {
            res.add(node.val);
            return;
        }
        getNodes(node.left, k - 1);
        getNodes(node.right, k - 1);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
