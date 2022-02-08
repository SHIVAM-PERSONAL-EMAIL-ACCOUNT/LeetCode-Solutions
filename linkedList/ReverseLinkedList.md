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
    
    public ListNode reverseList(ListNode head) {
        if (head == null) return null;
        ListNode first = head;
        ListNode oldHead = head;
        while (first.next != null) {
            oldHead = head;
            head = first.next;
            first.next = head.next;
            head.next = oldHead;
        }
        return head;
    }
}
```

### Time/Space Complexity

- Time Compelxity: O(n)
- Space Compelxity: O(1)
