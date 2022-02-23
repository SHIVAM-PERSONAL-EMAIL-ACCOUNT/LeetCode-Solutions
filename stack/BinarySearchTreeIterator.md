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
class BSTIterator {
    
    Deque<TreeNode> stack;
    TreeNode dummyNode;
    
    public BSTIterator(TreeNode root) {
        dummyNode = new TreeNode(-1, null, root);
        stack = new ArrayDeque<>();
        stack.push(dummyNode);
    }
    
    public int next() {
        if (stack.peek().right != null)
            return getRightChildLeftMost(stack.pop().right).val;
        else
            stack.pop();
        return stack.peek().val;
    }
    
    public TreeNode getRightChildLeftMost(TreeNode rightChild) {
        stack.push(rightChild);
        TreeNode curr = rightChild;
        while (curr.left != null) {
            curr = curr.left;
            stack.push(curr);
        }
        return curr;
    }
    
    public boolean hasNext() {
        return !(stack.peek().right == null && stack.size() == 1);
    }
}

/**
 * Your BSTIterator object will be instantiated and called as such:
 * BSTIterator obj = new BSTIterator(root);
 * int param_1 = obj.next();
 * boolean param_2 = obj.hasNext();
 */
```

### Time/Space Complexity

- Time Compelxity: O(1) average
- Space Compelxity: O(h) average
