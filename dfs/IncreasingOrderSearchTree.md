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
    
    public TreeNode increasingBST(TreeNode root) {
        TreeNode temp = new TreeNode(0, null, root);
        rearrange(root, temp);
        return temp.right;
    }
    
    public void rearrange(TreeNode node, TreeNode parent) {
        if (node == null) return;
        
        rearrange(node.left, node);
        rearrange(node.right, node);
        
        if (node.left == null) return;
        
        TreeNode rightMost = getRightMostOfLeftChild(node.left);
        
        TreeNode temp = node.left;
        node.left = null;
        rightMost.right = node;
        if (parent.left == node) parent.left = temp;
        else parent.right = temp;
    }
    
    public TreeNode getRightMostOfLeftChild(TreeNode node) {
        if (node.right == null) return node;
        return getRightMostOfLeftChild(node.right);
    }
}
```
### Time/Space Complexity

- Time Complexity: O(n<sup>2</sup>), for a left-skewed tree
- Space Complexity: O(n)
