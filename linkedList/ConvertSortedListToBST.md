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
    
    public TreeNode sortedListToBST(ListNode head) {
        return constructBST(head);
    }
    
    public TreeNode constructBST(ListNode head) {
        if (head == null)
            return null;
        
        if (head.next == null)
            return new TreeNode(head.val);
        
        ListNode prev, slow, fast, first, second;
        
        prev = head;
        slow = head;
        fast = head;
        while (fast != null && fast.next != null) {
            prev = slow;
            slow = slow.next;
            fast = fast.next.next;
        }
        
        TreeNode curr = new TreeNode(slow.val); 
        
        first = head;
        second = slow.next;
        prev.next = null;
        
        curr.left = constructBST(first);
        curr.right = constructBST(second);
        
        return curr;
    }    
}
```
### Time/Space Compelxity

- Time Complexity: O(n log n)
- Space Compelxity: O(log n)
