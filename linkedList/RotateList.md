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
    
    public ListNode rotateRight(ListNode head, int k) {
        if (k == 0) 
            return head;
        
        int len = 0;
        ListNode curr = head;
        
        while (curr != null) {
            ++len;
            curr = curr.next;
        }
        
        if (len <= 1 || k % len == 0) 
            return head;
        
        ListNode trail, lead;
        trail = lead = head;
        int i = k % len;
        
        while (i-- > 0)
            lead = lead.next;
        
        while (lead.next != null) {
            lead = lead.next;
            trail = trail.next;
        }
        
        lead.next = head;
        head = trail.next;
        trail.next = null;
        
        return head;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
