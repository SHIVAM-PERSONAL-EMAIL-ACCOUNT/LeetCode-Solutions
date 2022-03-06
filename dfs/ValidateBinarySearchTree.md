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
    
    public boolean isValidBST(TreeNode root) {
        return dfs(root, Long.MAX_VALUE, Long.MIN_VALUE);
    }
    
    public boolean dfs(TreeNode node, long MAX, long MIN) {
        if (node == null) return true;
        if (node.val >= MAX || node.val <= MIN) return false;
        return dfs(node.left, node.val, MIN) &&
               dfs(node.right, MAX, node.val); 
    }
}
```

### Time/Space Compelxity

- Time Complexity: O(n)
- Space Complexity: O(n) 
