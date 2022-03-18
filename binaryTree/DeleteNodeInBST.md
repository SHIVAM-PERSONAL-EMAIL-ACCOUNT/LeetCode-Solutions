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
    
    int successor = 0;
    
    public TreeNode deleteNode(TreeNode root, int key) {
        if (root != null && root.right == null && root.val == key) return root.left;
        search(root, null, key);
        return root;
    }
    
    public void search(TreeNode child, TreeNode parent, int key) {
        if (child == null) return;
        if (child.val > key) search(child.left, child, key);
        else if (child.val < key) search(child.right, child, key);
        else delete(child, parent);
    }
    
    public void delete(TreeNode nodeToBeDeleted, TreeNode parent) {
        if (nodeToBeDeleted.right == null) {
            if (parent.left == nodeToBeDeleted) parent.left = nodeToBeDeleted.left;
            else parent.right = nodeToBeDeleted.left;
            return;
        }
        if (nodeToBeDeleted.right.left == null) {
            successor = nodeToBeDeleted.right.val;
            nodeToBeDeleted.right = nodeToBeDeleted.right.right;
        }
        else {
            setSuccessor(nodeToBeDeleted.right, nodeToBeDeleted);
        }
        nodeToBeDeleted.val = successor;
    }
    
    public void setSuccessor(TreeNode curr, TreeNode parent) {
        if (curr.left == null) {
            successor = curr.val;
            parent.left = curr.right;
            return;
        }
        setSuccessor(curr.left, curr);
    }
        
}
```

### Time/Space Complexity

- Time Complexity: O(h)
- Space Complexity: O(h)
