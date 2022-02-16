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
    
    public int pairSum(ListNode head) {
        ListNode slow, fast, prev;
        int max = 0;
        
        slow = fast = prev = head;
        while (fast != null) {
            prev = slow;
            slow = slow.next;
            fast = fast.next.next;
        }
        
        prev.next = reverse(slow);
        
        slow = head;
        fast = prev.next;
        while (fast != null) {
            max = Math.max(max, slow.val + fast.val);
            slow = slow.next;
            fast = fast.next;
        }
        
        return max;
    }
    
    public ListNode reverse(ListNode head) {
        ListNode res = new ListNode(0, head);
        ListNode curr = head;
        while(curr.next != null) {
            ListNode temp = curr.next;
            curr.next = temp.next;
            temp.next = res.next;
            res.next = temp;
        }
        return res.next;
    }
}
```

### Time/Space Compelxity

- Time Complexity: O(n)
- Space Compelxity:O(1)
