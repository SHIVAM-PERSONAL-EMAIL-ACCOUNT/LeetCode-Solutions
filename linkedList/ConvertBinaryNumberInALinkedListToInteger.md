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
    
    public int getDecimalValue(ListNode head) {
        ListNode curr = head;
        int ans = 0;
        while (curr != null) {
            ans = (ans << 1) | curr.val;
            curr = curr.next;
        }
        return ans;
    }
}
```

### Time/Space Compelxity

- Time Complexity: O(n)
- Space Complexity: O(1)
