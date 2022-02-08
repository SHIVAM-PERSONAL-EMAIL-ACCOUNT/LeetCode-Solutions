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
    
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if (list1 == null && list2 == null) return null;
        if (list1 != null && list2 == null) return list1;
        if (list1 == null && list2 != null) return list2;
        
        ListNode ans = (list1.val <= list2.val) ? list1 : list2;
        
        ListNode head1 = list1;
        ListNode head2 = list2;
        while (head1 != null && head2 != null) {
            ListNode back = (head1.val <= head2.val) ? head1 : head2;
            ListNode front = (head1.val <= head2.val) ? head2 : head1;
            ListNode prev = back;
            while (back != null && back.val <= front.val) {
                prev = back;
                back = back.next;
            }
            if (head1.val <= head2.val) head1 = back;
            else head2 = back;
            prev.next = front;
        }
        
        return ans;
    }
}
```

### Time/Space Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
