### Solution

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
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
    
    public boolean isSubPath(ListNode head, TreeNode root) {
        return dfs(head, root);
    }
    
    public boolean dfs(ListNode head, TreeNode root) {
        if (root == null)
            return false;
        return check(head, root) ? true : 
               dfs(head, root.left) ||
               dfs(head, root.right);    
    }
    
    public boolean check(ListNode head, TreeNode root) {
        if (head == null)
            return true;
        
        if (root == null)
            return false;
        
        if (head.val != root.val)
            return false;
        
        return check(head.next, root.left) || 
               check(head.next, root.right);
    }
}
```

### Time/Space Compelxity

- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(n<sup>2</sup>)
