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
    public int [] nextLargerNodes(ListNode head) {
        if (head == null) return new int [] {};
        
        int size, i;
        ListNode curr;
        size = getSize(head);
        head = reverse(head);
        int [] ans = new int [size];
        Deque<Integer> stack = new ArrayDeque<>();
        stack.push(head.val);
        ans[0] = 0;
        
        curr = head.next;
        i = 0;
        while (curr != null) {
            int val = curr.val;
            while (!stack.isEmpty() && stack.peek() <= val)
                stack.pop();
            if (stack.isEmpty()) 
                ans[++i] = 0;
            else 
                ans[++i] = stack.peek();
            stack.push(curr.val);
            curr = curr.next;
        }
        
        reverse(ans);
        return ans;        
    }
    
    public int getSize(ListNode head) {
        int size = 0;
        ListNode curr = head;
        while (curr != null && ++size > 0)
            curr = curr.next;
        return size;
    }
    
    public void reverse(int [] ans) {
        int i = 0, j = ans.length - 1;
        while(i < j) {
            int temp = ans[i];
            ans[i] = ans[j];
            ans[j] = temp;
            i++;
            j--;
        }
    }
    
    public ListNode reverse(ListNode head) {
        ListNode finalHead, temp, curr;
        finalHead = curr = head;
        while (curr.next != null) {
            temp = curr.next;
            curr.next = temp.next;
            temp.next = finalHead;
            finalHead = temp;
        }
        return finalHead;
    }   
}
```

### Time/Space Compelxity

- Time Compelxity: O(n)
- Space Compelxity: O(n)
