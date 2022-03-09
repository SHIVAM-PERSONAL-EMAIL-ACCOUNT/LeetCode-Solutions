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
    
    public TreeNode convertBST(TreeNode root) {
        if (root == null) return null;
        traverse(root, 0);
        return root;
    }
    
    public int traverse(TreeNode node, int sum) {
        if (node.right != null)
            sum = traverse(node.right, sum);
        
        node.val += sum;
        sum = node.val;
        
        if (node.left != null)
            sum = traverse(node.left, sum);
        
        return sum;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
