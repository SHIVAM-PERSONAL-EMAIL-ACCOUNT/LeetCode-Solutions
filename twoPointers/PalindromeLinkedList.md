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
    
    public boolean isPalindrome(ListNode head) {
        ListNode reversedHead = reversedList(head);
        ListNode curr = head, revCurr = reversedHead;
        while (curr != null) {
            if (curr.val != revCurr.val) return false;
            curr = curr.next;
            revCurr = revCurr.next;
        }
        return true;
    }
    
    public ListNode reversedList(ListNode head) {
        ListNode curr = head.next, reversedHead = new ListNode(head.val);
        while (curr != null) {
            ListNode temp = new ListNode(curr.val, reversedHead);
            reversedHead = temp;
            curr = curr.next;
        }
        return reversedHead;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
