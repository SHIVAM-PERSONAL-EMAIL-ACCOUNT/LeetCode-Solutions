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
    public boolean isSymmetric(TreeNode root) {
        return (root.left == null && root.right == null) || check(root.left, root.right);
    }
    
    public boolean check(TreeNode left, TreeNode right) {
        Deque<TreeNode> leftS = new ArrayDeque<>(); 
        Deque<TreeNode> rightS = new ArrayDeque<>();
        TreeNode currLeft = left;
        TreeNode currRight = right;
        do {
            if (currLeft == null && currRight != null) return false;
            if (currLeft != null && currRight == null) return false;
            if (currLeft != null && currLeft.val != currRight.val) return false;
            if (currLeft == null) {
                TreeNode nodeL = leftS.pop();
                TreeNode nodeR = rightS.pop();
                currLeft = nodeL.right;
                currRight = nodeR.left;
            }
            else {
                leftS.push(currLeft);
                rightS.push(currRight);
                currLeft = currLeft.left;
                currRight = currRight.right;
            }
        }
        while (currLeft != null || currRight != null || !leftS.isEmpty() || !rightS.isEmpty());
        return true;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
