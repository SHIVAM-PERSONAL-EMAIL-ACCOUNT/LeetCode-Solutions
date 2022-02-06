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
    
    TreeNode prev = null;
    int min = Integer.MAX_VALUE;
    
    public int getMinimumDifference(TreeNode root) {
        traverse(root);
        return min;
    }
    
    public void traverse(TreeNode node) {
        if (node == null) return;
        
        traverse(node.left);
        
        if (prev != null)
            min = Math.min(min, Math.abs(prev.val - node.val));
        
        prev = node;
        
        traverse(node.right);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
