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
    
    public TreeNode insertIntoBST(TreeNode root, int val) {
        if (root == null) return new TreeNode(val);
        TreeNode head = root;
        TreeNode prev = root;
        TreeNode curr = root;
        while(curr != null) {
            prev = curr;
            if (curr.val > val)curr = curr.left;
            else curr = curr.right;
        }
        if (val > prev.val) prev.right = new TreeNode(val);
        else prev.left = new TreeNode(val);
        return head;
    }
}
```

### Time/Space Compelxity

- Time Complexity: O(log n)
- Space Complexity: O(1)
