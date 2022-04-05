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
    
    int max = 0;
    
    public int longestUnivaluePath(TreeNode root) {
        int length = dfs(root) - 1;
        if (length > max) max = length;
        return max;
    }
    
    public int dfs(TreeNode node) {
        if (node == null) return 0;
        int left = dfs(node.left);
        int right = dfs(node.right);
        if (left == 0 && right == 0) return 1;
        if (left != 0 && right != 0) {
            if (node.val != node.left.val && node.val != node.right.val) return 1;
            if (node.val == node.left.val && node.val == node.right.val) {
                if (left + right > max) max = left + right;
                return Math.max(left,right) + 1;
            }
            if (node.val == node.left.val) {
                if (max < left) max = left;
                return left + 1;
            }
            else {
                if (max < right) max = right;
                return right + 1;
            }
        }
        if (left != 0) {
            if (node.val == node.left.val) {
                if (max < left) max = left;
                return left + 1;
            }
            return 1;
        }
        else {
            if (node.val == node.right.val) {
                if (max < right) max = right;
                return right + 1;
            }
            return 1;
        }
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
