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
    
    public boolean isBalanced(TreeNode root) {
        return check(root);
    }
    
    public boolean check(TreeNode node) {
        if (node == null) return true;
        if (Math.abs(height(node.left) - height(node.right)) > 1) return false;
        return check(node.left) && check(node.right);    
    }
    
    public int height(TreeNode node) {
        if (node == null) return 0;
        return Math.max(height(node.left) + 1, height(node.right) + 1);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
