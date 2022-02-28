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
    
    public TreeNode constructMaximumBinaryTree(int [] nums) {
        TreeNode head, last;
        head = last = null;
        Deque<TreeNode> stack = new ArrayDeque<>();
        int len = nums.length;
        for (int i = 0; i < len; i++) {
            while (!stack.isEmpty() && stack.peek().val < nums[i])
                last = stack.pop();
            if (stack.isEmpty()) {
                TreeNode newParent = new TreeNode(nums[i], last, null);
                stack.push(newParent);
                head = newParent;
            }
            else {
                stack.peek().right = new TreeNode(nums[i], last, null);
                stack.push(stack.peek().right);
            }
            last = null;
        }
        return head;
    }
}
```

### Time/Space Complexity

- Time Compelxity: O(n)
- Space Compelxity: O(n)
