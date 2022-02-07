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
    
    public TreeNode mergeTrees(TreeNode root1, TreeNode root2) {
        TreeNode ans = traverse(root1, root2);
        return ans;
    }
    
    public TreeNode traverse(TreeNode node1, TreeNode node2) {       
        if (node1 == null && node2 == null) return null;
        
        int val1 = (node1 == null) ? 10001 : node1.val;
        int val2 = (node2 == null) ? 10001 : node2.val;
        
        int sum = 0;
        if (val1 != 10001) sum += val1;
        if (val2 != 10001) sum += val2;
        TreeNode newNode = new TreeNode(sum);
        
        if (val1 == 10001 && val2 != 10001) {
            newNode.left = traverse(null, node2.left);
            newNode.right = traverse(null, node2.right);
        }
        else if (val1 != 10001 && val2 == 10001) {
            newNode.left = traverse(node1.left, null);
            newNode.right = traverse(node1.right, null);
        }
        else {
            newNode.left = traverse(node1.left, node2.left);
            newNode.right = traverse(node1.right, node2.right);
        }
        
        return newNode;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(m + n)
- Space Complexity: O(m + n)
