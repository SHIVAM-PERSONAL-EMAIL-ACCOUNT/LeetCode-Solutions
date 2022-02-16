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
    
    public ListNode reverseBetween(ListNode head, int left, int right) {
        ListNode curr, prev;
        ListNode temp = new ListNode(-1, head);
        int  i = -1;
        
        curr = temp;
        while (++i < left - 1)
            curr = curr.next;
        
        curr.next = reverse(curr.next, right - left + 1);
        
        return temp.next;
    }
    
    public ListNode reverse(ListNode head, int right) {
        ListNode prev, curr, last;
        prev = null;
        last = head;
        curr = head;
        while (right-- > 0) {
            ListNode temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        last.next = curr;
        return prev;
    }
}
```

### Time/Space Complexity

- Time Compelxity: O(n)
- Space Compelxity: O(1)
