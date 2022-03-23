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
    
    int maxDiff = 0;
    
    public int maxAncestorDiff(TreeNode root) {
        calculateMaxAncestorDiff(root, root.val, root.val);
        return maxDiff;
    }
    
    public void calculateMaxAncestorDiff(TreeNode node, int min, int max) {
        if (node == null) return;
        maxDiff = Math.max(maxDiff, Math.abs(node.val - max));
        maxDiff = Math.max(maxDiff, Math.abs(node.val - min));
        min = Math.min(min, node.val);
        max = Math.max(max, node.val);
        calculateMaxAncestorDiff(node.left, min, max);
        calculateMaxAncestorDiff(node.right, min, max);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
