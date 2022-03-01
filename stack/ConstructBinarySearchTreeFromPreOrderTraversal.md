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
    
    public TreeNode bstFromPreorder(int [] preOrder) {
        Deque<TreeNode> stack = new ArrayDeque<>();
        stack.push(new TreeNode(preOrder[0]));
        TreeNode head = stack.peek();
        for (int i = 1; i < preOrder.length; i++) {
            TreeNode parent = stack.peek();
            while (!stack.isEmpty() && stack.peek().val < preOrder[i])
                parent = stack.pop();
            if (parent.val < preOrder[i]) {
                parent.right = new TreeNode(preOrder[i]);
                stack.push(parent.right);
            }
            else {
                parent.left = new TreeNode(preOrder[i]);
                stack.push(parent.left); 
            }
        }
        return head;
    }
}
```

### Time/Space Complexity

- Time Compelxity: O(n)
- Space Compelxity: O(n)
