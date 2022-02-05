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
    
    public int minDepth(TreeNode root) {
        return compute(root);
    }
    
    public int compute(TreeNode node) {
        if (node == null) return 0;
        
        if (node.left == null && node.right == null) return 1;
        
        int leftDepth = compute(node.left);
        int rightDepth = compute(node.right);
        
        if (leftDepth == 0) return rightDepth + 1;
        else if (rightDepth == 0) return leftDepth + 1;
        else return Math.min(leftDepth + 1, rightDepth + 1);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
