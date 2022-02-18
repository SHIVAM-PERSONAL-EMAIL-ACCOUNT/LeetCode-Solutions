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
    
    public ListNode [] splitListToParts(ListNode head, int k) {
        int size, i, j;
        
        size = getSize(head);
        int [] distribution = getDistribution(size, k);
        ListNode [] ans = new ListNode [k];
        
        i = 0;
        while(i < k) {
            if (distribution[i] == 0)
                break;
            ListNode part = new ListNode(head.val);
            ListNode partPtr = part;
            head = head.next;
            j = 1;
            while(j < distribution[i]) {
                partPtr.next = new ListNode(head.val);
                head = head.next;
                partPtr = partPtr.next;
                j++;
            }
            ans[i] = part;
            i++;
        }
        
        while(i < k) {
            ans[i] = null;
            i++;
        }
        
        return ans;
    }
    
    public int getSize(ListNode head) {
        ListNode curr = head;
        int size = 0;
        while (curr != null && ++size > 0)
            curr = curr.next;
        return size;
    }
    
    public int [] getDistribution(int size, int k) {
        int [] distribution = new int [k];
        int capacity = size/k;
        if (capacity == 0) {
            Arrays.fill(distribution, 0, size, 1);
            return distribution;
        }
        Arrays.fill(distribution, capacity);
        int extras = size % k;
        Arrays.fill(distribution, 0, extras, capacity + 1);
        return distribution;
    }
}
```
### Time/Space Compelxity

- Time Compelxity: O(n)
- Space Compelxity: O(k)
