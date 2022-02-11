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
class Solution {
    
    public ListNode removeElements(ListNode head, int val) {
        ListNode temp = new ListNode(val - 1, head);
        traverse(temp, val);
        return temp.next;
    }
    
    public void traverse(ListNode node, int val) {
        if (node.next == null)
            return;
        if (node.next.val == val) {
            node.next = node.next.next;
            traverse(node, val);
        }
        else traverse(node.next, val);
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
