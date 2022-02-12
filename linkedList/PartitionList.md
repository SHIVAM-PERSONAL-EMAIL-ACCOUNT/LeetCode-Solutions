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
    
    public ListNode partition(ListNode head, int x) {
        if (head == null || head.next == null) return head;
        ListNode first = new ListNode(0);
        ListNode second = new ListNode(0);
        ListNode headPt = head;
        ListNode firstPt = first;
        ListNode secondPt = second;
        while (headPt != null) {
            if (headPt.val >= x) {
                secondPt.next = new ListNode(headPt.val);
                secondPt = secondPt.next;
            }
            else {
                firstPt.next = new ListNode(headPt.val);
                firstPt = firstPt.next;
            }
            headPt = headPt.next;
        }
        firstPt.next = second.next;
        return first.next;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)
